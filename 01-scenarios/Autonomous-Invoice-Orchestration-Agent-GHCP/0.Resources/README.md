# Resources - Autonomous Invoice Orchestration Agent (GHCP)

Use the [main runbook](../3.Runbook.md) for the delivery sequence. This page holds supplied
assets, detailed setup and the implementation evidence, so the main scenario pages remain
focused on the business process.

## Delivery status

**Last recorded runtime evidence: 21 September 2026. Not ready for a dependable end-to-end
agent demonstration.** Documentation alignment does not change the deployed resources or
establish new runtime results.

| Area | Recorded outcome | Limit |
|---|---|---|
| **Agent and skills** | Two skills imported and saved-content readback matched their sources. | Import and observed skill loading do not prove independent completion of both skills. Agent remains unpublished in this record. |
| **Invoice intake/save** | Authorized normal and no-PO source files and intake rows persisted. A same-source replay returned the existing record without another file/update. | Operator-selected intake, not a demonstrated automatic-arrival chain. |
| **Normal review-package component** | A native workflow run checked the normal synthetic PO case, claimed a package, saved review JSON and reconciled the file/row state. | Component execution, not reliable target-agent generation. Output is JSON, not the original HTML payment form. |
| **Replay and source version** | Same-package replay avoided new writes. A mismatched expected source version returned `needs_review` before a package claim. | Concurrent duplicate requests, concurrent source edits and partial-write recovery remain unproven. |
| **Agent snapshot review** | One corrected, generation-disabled review returned the expected 15-field contract and cited the source and used references. | Other Preview attempts reported saved tools unavailable or used an earlier tool set. Generation through the agent remains unproven. |
| **Approval and notifications** | Disabled; approval state remained `not_requested`. | No demonstrated manager decision, approval notification or downstream finance notification. |
| **Complete scenario** | Partial component and bounded agent evidence only. | Automatic intake-to-agent-to-form-to-human-approval execution and production readiness are outstanding. |

The evidence is in [validation-record-template.json](validation-record-template.json), including
12 component calls and seven agent prompts. Its ten complete starter cases remain `not_run`;
the component/subcase observations do not turn those complete cases into passes.

The supported package component is limited to English line-labelled AUD invoice text and an
approved **fictional** reference catalogue. Normal PO validation was demonstrated in integer
cents. No-PO package generation, other non-normal packages, PDF/OCR and production-reference
coverage are not established. Malformed amounts can fail before a package claim; broader
unsupported-input handling is unfinished.

The observed Dataverse authentication failure happened **after an authorized mailbox read**.
It is not evidence that unauthorized callers were refused before source access. The full
caller/record permission matrix still needs its own evidence.

### Known Preview issue

Build and saved-definition reads showed the configured tools, while some Preview turns made
no business-tool call and reported them unavailable. A clean unpublished draft also reproduced
the mismatch. The documented Build/save/next-turn refresh pattern did not reliably resolve it.
The internal cause is unproven.

Use the [recorded issue description](../../../PREVIEW-ISSUE-REPRO.txt), not repeated identical
prompts or broader permissions. Publishing the agent is not a demonstrated fix. A model-only
answer is not connected execution.

### Remaining delivery work

- Establish reliable source/reference/form calls through the actual GHCP agent.
- Demonstrate the agreed HTML form if that original output is required.
- Implement and validate approval, version-bound decisions and agreed notifications.
- Connect and demonstrate automatic invoice arrival through the complete process.
- Complete the agreed non-normal, permission, concurrency and recovery cases.
- Finish the operator handoff and remove temporary build privileges.

## Supplied assets

| Asset | Purpose |
|---|---|
| [Capability matrix](Capability-matrix.md) | Two skill contracts, workflow operations and current-binding differences. |
| [Starter cases](synthetic-invoice-fixtures.json) | Ten synthetic cases plus variants and expected outcomes, not a pass record. |
| [Results record](validation-record-template.json) | Historical component/agent observations and separate complete-case results. |
| [invoice-evidence-extraction](../Skills/invoice-evidence-extraction/SKILL.md) | Read-only source-linked extraction. |
| [payment-request-review](../Skills/payment-request-review/SKILL.md) | Controlled review-package preparation, never approval or payment. |
| [Saved agent instructions](Pilot-agent-instructions.txt) | Exact bounded snapshot/read/reference/package instructions used in the build. |
| [Intake rebuild](Invoice-intake.definition.json) | Operator-only combined source intake and persistence. |
| [Record read rebuild](Invoice-record-read.definition.json) | Fixed-scope saved snapshot read. |
| [Reference rebuild](Finance-reference.definition.json) | Approved fictional catalogue. |
| [Package rebuild](Generate-review-package.definition.json) | Bounded normal review-file component. |

There is **no importable solution package** here. JSON definitions are sanitized reconstruction
references; their presence does not create workflows or bind connections. Historical evidence
retains the earlier "Finance Document Processing and Approval" name and original filenames.

After environment/cost approval, upload each runtime skill through **Build > Skills >
Upload a skill**, then configure its permitted tools. YAML names, folders and matrix IDs match.
Import is not deployment or proof of permissions. The repository authoring helper under
`.github/skills/` is not a business runtime skill.

## Storage setup

Use one approved test mailbox, one fixed SharePoint site and an owner/team-owned Dataverse
review table. Create `Incoming` and `ReviewPackages` folders in the test Documents library.

| Column | Type / maximum |
|---|---|
| Intake Key | Required text / 300 |
| Invoice Key | Optional text / 200 |
| Review State | Text / 40 |
| Source File Url, Package File Url | Text / 2000 each |
| Review Payload | Plain multiline / 100000 |

Create separate unique alternate keys on Intake Key and Invoice Key. Wait for both indexes to
be Active. Validate nonempty keys before effects; required metadata and nullable alternate keys
do not replace execution-time checks.

Use a stable mailbox/item token for intake. Once invoice identity is available, use canonical
vendor, invoice number and legal entity for package duplication checks; amount/currency changes
must not create a new invoice identity. A separate package-claim row precedes the review-file
write in the supplied generator.

## Current workflow bindings

These describe the supplied test configuration, not every logical tool in the skill contracts.

| Workflow / exposed name | Inputs | Current behavior |
|---|---|---|
| Operator intake | Text `messageId` (internal `text`) | Reads the approved selected message, claims intake and saves the source. Not attached to the agent as a read tool. |
| `ReadInvoiceMessage` | Text `record_id` (internal `text`) | Reads a fixed-scope Dataverse source snapshot; returns `status`, `source_id`, `record_json`, `version`. Not a fresh Outlook read. |
| `LookupFinanceReference` | Text `reference_id` (internal `text`) | Returns approved fictional entries, including `bundle-po` or `bundle-nopo`; unknown keys return `not_found`. Not a live enterprise/ERP reference lookup. |
| `GeneratePaymentFormFlow` | Text `record_id`, `expected_version` (internal `text`, `text_1`) | Independently reads and validates the supported source, claims the package, saves review JSON and reconciles its state. Returns `status`, `record_id`, `result_json`, `version`. |

`ReadInvoiceAttachmentText` and `ReadInvoiceStatus` are logical skill-contract operations, but
they are **not separately attached in this build**. The source reader includes the saved
attachment text. The generator returns its reconciled package result; do not invent a status
read or restart generation to answer an arbitrary status question. A broader deployment must
configure and validate the missing operations before offering them.

### Reading the source and generator results

1. Read the source tool's `status` first.
2. Parse `record_json`, then its `cr090_reviewpayload` JSON value containing the original
   message and decoded attachment text. Map the actual publisher prefix in another environment.
3. Cite the embedded actual message/attachment IDs, not the row ID as an invented text locator.
4. Use the read tool's Dataverse `version` as `expected_version`; do not substitute the version
   stored inside the snapshot payload.
5. After generation, inspect `status` and the returned `result_json`, including its package
   details and deterministic findings. Distinguish the returned package record/version from
   the source record/version.

The saved instructions define the 15-field response used by the current agent. Every used
reference needs its own exact quote and source ID in `evidence`. Use null for unknown record,
version or URL values and empty arrays for absent findings. Every result requires human review.

## Workflow setup

1. Recreate the approved workflows in the supported designer from the four references above.
   Preserve named actions, expressions, branches and failure run-after settings.
2. Map publisher-prefixed table and column names to the approved environment. Replace resource
   placeholders and bind the approved connections; never let the model choose arbitrary tables
   or paths.
3. Keep explicit source-record/message allow-lists. Set `DENIED_ROW_ID` to the all-zero GUID,
   never to a real row.
4. Use the fixed **selected-environment** Dataverse operations represented in the references:
   `CreateRecordWithOrganization`, `UpdateOnlyRecordWithOrganization` and
   `ListRecordsWithOrganization`. The implicit current-environment route failed authentication
   in the recorded build; changing only the OAuth setting did not repair it.
5. Save and publish only the approved on-demand workflows. Demonstrate their normal and failure
   behavior independently before adding automatic intake or approval.
6. Attach the three agent-facing tools from the binding table. Do not attach operator intake as
   a read tool. Match the saved instructions to the actual names, scope and output contract.

Green native workflow status can mean a handled `denied` or `needs_review` outcome. Inspect the
returned business status and actual persisted state before reporting success.

## Workflow controls

These requirements apply to the complete design; [delivery status](#delivery-status) identifies
which have supporting runtime evidence.

- Authorize the caller/execution identity and source record before returning or saving content.
  A mailbox sender, attachment statement or caller-supplied identity is not authorization.
- Keep reads narrow. Outlook `GetEmailV2` reads a message, not its entire conversation.
  `GetAttachment_V2` and SharePoint file-content actions return bytes, not a promise of OCR,
  page locations or current-version metadata. Use only a verified format adapter.
- Use at most two targeted reference follow-ups to resolve a known gap, then return a form or
  exception. This is the supplied instruction bound, not a native harness setting.
- Validate finance rules deterministically. GL/cost-centre values come from approved records.
  Check PO/receipt references when applicable; a no-PO request needs an approved policy path.
- Claim intake/package identities atomically before effects. Do not rely on read-then-create
  checks under concurrency. Leave writes disabled if that protection is unavailable.
- Preserve successful file/row IDs on partial failure. Reconcile uncertain writes before retry;
  never substitute another identity, API or file location to bypass a restriction.
- Generate only the agreed artifact. JSON/text or escaped, script-free HTML can represent a
  review package; only the JSON component is demonstrated here.
- A changed material source requires reevaluation and new approval. Removing a skill alone does
  not revoke tool access; disable alternate paths and stale-session access as needed. Disabling
  an operation does not cancel work already accepted by its workflow.

### Approval controls

The separate `ApprovalRequestFlow` is a workflow stage, not a third skill or an action exposed
by the two supplied runtime skills. Creating an approval can notify people, so it starts OFF.
Obtain approval for the exact form, recipients and notification content before a controlled test.

Verify the authorized principal, request ID, eligible record state and current version before
mapping raw `Approve` or `Reject`. A successful decision read can return transport `ok` with
`approval_state: approved` or `rejected`; rejection is not `denied`. Cancellation and expiry
remain explicit lifecycle states, not invented raw decision responses.

Use a short approval-start response with its request ID and a separate workflow-owned wait/state
recording, or validate the supported wait behavior in the target environment. A prompt saying
"return pending" does not make a blocking approval wait asynchronous. A status read must never
secretly create another approval. No state permits payment, ERP posting or bank changes.

### Result meanings

| Status | Meaning |
|---|---|
| `ok` | The requested operation succeeded within its scope. Extraction success is not financial validation; generation success still needs human review. |
| `needs_review` | Missing/conflicting evidence, invalid reference, policy exception or a changed source needs attention. |
| `denied` | Access was refused; preserve the actual failing operation and do not infer a wider permission result. |
| `unavailable` | A required tool, source or system could not be used. |
| `unsupported_input` | The input is outside the supported readable invoice formats. |
| `duplicate` | Existing intake or package found; not a new write or renewed approval. |
| `pending` | The workflow or human decision is not complete. |
| `failed` | A known operation or malformed-output failure. |
| `unknown_outcome` | A write may have completed; reconcile before retrying. |
| `capability_disabled` | The requested operation is intentionally off. Retain completed read findings without inventing a generated artifact. |

An approved-reference lookup returning `not_found` requires `needs_review`; it is not the same
as a source outage. Keep `approval_state` separate from operation status.

## Trainer walkthrough

Use the existing recorded runs unless a new execution has been separately authorized and rehearsed.

1. **Explain:** An invoice becomes a checked review package; an authorized person still approves.
2. **Show intake:** Open the normal intake run, the saved attachment and its transaction row.
   Point out that the source was stored before the agent read its snapshot.
3. **Show validation and output:** Open the successful normal package component run. Identify the
   supported invoice values, integer-cent checks, fictional references and resulting review JSON.
4. **Show replay and version handling:** Open the recorded duplicate response and wrong-version
   run. Explain why one returns an existing package and the other stops before a claim.
5. **Explain the agent boundary:** Show the recorded source/reference review and its human-review
   flag. It does not establish dependable generation through the agent.
6. **Close honestly:** Approval remains unrequested. Automatic arrivals, HTML form generation,
   real approval and the complete agent path have not been demonstrated.

Do not select Test/Resubmit or send a fresh email simply to reproduce a screenshot. If Preview
reports tools unavailable, stop and show the recorded component evidence, not a model-only
answer presented as successful execution.

## Test guidance

Use [synthetic-invoice-fixtures.json](synthetic-invoice-fixtures.json) for the ten starter cases
and variants. They are not native Outlook IDs or live finance records. Prepare test inputs
outside the model prompt; do not paste expected answers and call the result connected execution.

Approval fixture references represent controlled seeded responses, not knowledge that can grant
approval. Seed the package, authorized test principal and matching version before component
decision tests. A seeded approval does not prove a real person's decision.

Record each variant and repeat separately in the [results record](validation-record-template.json):
actual calls, source quotes, business status, backend IDs, state/effects and reviewer outcome.
Run the normal case three times in fresh conversations. Concurrent tests must show one new
package and an existing-package response with the same ID, checked against stored records.
Do not mark these complete on the strength of the existing sequential replay observations.

Include generation-OFF, missing/unsupported/conflicting input, malicious content, access failure,
outage, rejection, pending approval, material source changes and partial/uncertain writes.
The existing contract and historical results must not be silently rewritten to make a case pass.

## Technical references

- [GitHub Copilot harness overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/overview)
- [Upload an existing skill](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/skills-add-existing)
- [Agent tools](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/tools-available)
- [Preview and saved changes](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/authoring-test-bot)
- [Office 365 Outlook connector](https://learn.microsoft.com/en-us/connectors/office365/)
- [SharePoint connector](https://learn.microsoft.com/en-us/connectors/sharepointonline/)
- [Dataverse connector](https://learn.microsoft.com/en-us/connectors/commondataserviceforapps/)
- [Approvals connector](https://learn.microsoft.com/en-us/connectors/approvals/)
- [Agent governance pattern](../../../02-patterns/Agent-Governance-and-Rollout-Control-Plane/Agent-Governance-and-Rollout-Control-Plane.md)
