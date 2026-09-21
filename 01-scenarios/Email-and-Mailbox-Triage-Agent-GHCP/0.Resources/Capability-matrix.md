# Capability Matrix

This matrix describes the **supplied review-only components**. The four scenario pages also
cover the end-to-end delivery design; arrival-driven intake and downstream actions are not
enabled by these resources. See [delivery status](README.md#delivery-status).

## Shared controls and status

All rows require the approved test environment, applicable permissions/capacity and a named reviewer. Microsoft authentication and fixed resource scope must be enforced before returning content. Connection identity is not email sender identity. Skill text grants no permission.

All outputs require human **review**, including `ok`; review does not authorize sending. Use `needs_review` for gaps/conflicts, `denied` for access refusal, `unavailable` for outages, `unsupported_input` for unsupported files, `failed` for malformed tool results, and `capability_disabled` for disabled actions. `not_run` is test status, not a runtime outcome.

Two read-only workflows and skills installed; 26 Preview prompts. Actual and
fault-assisted evidence is recorded separately. Effective denial and full acceptance
remain open. See [results](Actual-test-record.json).

## Included skill capabilities

| Capability ID / runtime file | Purpose and tool set | Dependencies and outcome |
|---|---|---|
| [shared-mailbox-intake](../Skills/shared-mailbox-intake/SKILL.md) | Read/assess one request using `ReadSharedMailboxMessage`, conditional `ReadSharedMailboxAttachmentText`, conditional `LookupApprovedReference` or configured knowledge | Current access plus readable evidence; outputs category, gaps and sources without writes |
| [grounded-reply-drafting](../Skills/grounded-reply-drafting/SKILL.md) | Produce draft text using accessible evidence; same permitted reads if needed | Authorized source input, not mandatory prior skill activation; output for human review, no save/send |

These IDs match folders and YAML names. Technical reads below support those
two capabilities; they are not additional generated skills. Deferred actions
have no skill and cannot be enabled merely by importing these two files.

| Local profile | Enabled skill capabilities | Tool exposure |
|---|---|---|
| Intake only | `shared-mailbox-intake` | Approved reads only; no reply preparation |
| Review draft | Both included IDs | Approved reads and ordinary response output; no mutations |

Profiles are deployment choices, not native harness switches. Conditional
attachment/knowledge dependencies activate only when that evidence is needed;
missing/disabled dependencies remain explicit. Remove access through all tool
paths on disable, recheck stale sessions, and keep shared read tools needed by
the other capability. A skill is not an access-control mechanism.

## Supporting operations and deferred actions

| Capability and boundary | Inputs -> outputs | Skill/procedure and real operation | Permissions, dependencies and human gate | Enable/disable, failures and evidence |
|---|---|---|---|---|
| Selected message read, not a conversation search | Fixed mailbox/item ID -> body, quoted history, attachment IDs | `shared-mailbox-intake`; pilot `ReadSharedMailboxMessage` label maps to Outlook **Get email (V2)** (`GetEmailV2`) | Delegated account with shared-mailbox rights; caller authorized before read; no service-principal Outlook connection | Enable only fixed approved mailbox. Denied returns no content; log item ID, connection identity and actual flow/agent trace. |
| Attachment text, no OCR | Message/attachment IDs -> text/source or explicit failure | `shared-mailbox-intake`; pilot GetEmailV2 + Select/base64ToString; GetAttachment_V2 is an alternative | Fixed-mailbox read; up to five non-inline .txt files <=64KB each | Actual text and unsupported binary tested. Unsupported -> `unsupported_input`; malformed projection -> `failed`. No separate attachment tool deployed. |
| Approved knowledge, no arbitrary URLs | Question or approved source key -> supporting text/source or no match | Both skills; configured native knowledge, or fixed SharePoint **Get file content** (`GetFileContent`) / **Get file content using path** (`GetFileContentByPath`) | Source entitlement must be verified; no inferred M365-wide access | Remove/block source access to disable. Missing -> review; denied/outage preserved. Cite exact evidence, not invented version metadata. |
| Response draft and route recommendation only | Evidence/category/gaps -> draft text, route suggestion and citations | Both skills; ordinary agent response, no write tool | Depends on accessible evidence; every result reviewed. Consequential correspondence has no substantive draft | No external effect. Record Preview trace, source calls and outcome. Unavailable evidence cannot become a confident answer. |
| Optional test task, deferred | Approved payload and idempotency token -> test record ID/readback | Separate fixed flow using Dataverse **Add a new row** (`CreateRecord`); neither skill needs it initially | Dedicated test table and scoped create/readback rights; explicit write approval | Disabled. Before enabling, require atomic duplicate prevention and timeout reconciliation; unknown write stays `unknown_outcome`. |
| Optional mailbox draft, deferred | Approved recipient/subject/body -> new draft ID | Separate restricted Graph `POST /users/{mailbox}/messages`, not threaded reply | Delegated `Mail.ReadWrite.Shared` plus mailbox rights; exact-preview approval | Disabled. Permission exceeds draft-create, so restrict operation/schema and block alternate endpoints. Reconcile before retry; never send. |
| Send/forward/delete/archive/move/mark-read/document delivery | Any such request -> `capability_disabled` | No action attached | No authorization granted by this draft | Check all tool paths, not just skills. Test attempts cause no effects; retain denial evidence. |

Use the [runbook](../3.Runbook.md), [architecture](../2.Architecture.md) and
[workflow setup](README.md#workflow-setup) for source links and connection details.
