# Capability Matrix - Autonomous Invoice Orchestration Agent (GHCP)

This is the **earlier text-pilot matrix**, preserved for reference. It is not the component
checklist for the simplified PDF path. Start with the [main runbook](../3.Runbook.md), which
keeps the original supporting flows and proposes one small `invoice-review` skill.
See [current delivery status](README.md#delivery-status) before relying on the dated details below.

The existing skill payloads and tool contracts remain unchanged. They cannot be relabelled
as compatible with `ParseInvoiceFlow` without adapting and validating their inputs.

<details>
<summary>Earlier two-skill test implementation</summary>

## Status and controls

Normal intake/package components, replay and version gates demonstrated.
Agent snapshot review passed once after corrections; subsequent runs claimed
tools unavailable. End-to-end readiness is blocked. Imported skills alone
do not prove execution. See [delivery status](README.md#delivery-status) for the
recorded scope and remaining work.

Require approved test resources, capacity, fixed mailbox/library/table scope and
authenticated caller authorization **before** reading/saving. Email is not
authority. All packages need human review. No generic CRUD/HTTP, payment, posting,
bank action or unapproved notification is exposed.

## Included skill capabilities

The table describes the logical skill contracts. In the supplied snapshot-based build,
`ReadInvoiceMessage` reads the stored message/attachment payload. No separate
`ReadInvoiceAttachmentText` or `ReadInvoiceStatus` tool is attached; the generator
returns its reconciled package result. Do not claim these unconfigured calls occurred.
See [current workflow bindings](README.md#current-workflow-bindings).

| Capability ID / file | Tool set | Inputs -> outputs; dependencies |
|---|---|---|
| [invoice-evidence-extraction](../Skills/invoice-evidence-extraction/SKILL.md) | `ReadInvoiceMessage`, `ReadInvoiceAttachmentText` | Selected source -> cited candidates; current read permission, no save/approval |
| [payment-request-review](../Skills/payment-request-review/SKILL.md) | `LookupFinanceReference`, `GeneratePaymentFormFlow`, `ReadInvoiceStatus` | Cited facts and authorized record/version -> form/exception; reference access, safe declared writes and readback |

IDs match YAML names and folders. Supporting workflow steps are not extra
skills. Approval remains a separate human-controlled process, not a hidden tool
invocation by either skill.

| Local deployment profile | Skill set | Effects |
|---|---|---|
| Evidence only | `invoice-evidence-extraction` | Read-only; never invokes intake/save |
| Connected package | Both IDs | Explicit test intake/save and form workflows; approval start OFF |

Profiles are design choices, not native harness switches. Package generation is
declared composite work, not "create-only": SharePoint creation and Dataverse
updates need permission together. Unlisted actions stay OFF. Disable alternate
paths and stale-session access too, preserving shared reads still needed.
Disabling does not cancel accepted backend work.

## Supporting workflow operations

The mappings below describe implementation choices for the complete scenario, not a
list of native GHCP tools or supplied exports. The recorded build uses the fixed
selected-environment Dataverse operations in [workflow setup](README.md#workflow-setup)
and a fictional reference catalogue rather than live finance reference tables.

| Operation and in/out | Actual implementation | Access, gate, failures and evidence |
|---|---|---|
| Read selected invoice -> body/attachment IDs | Outlook `GetEmailV2`; `ReadInvoiceMessage` stays read-only | Delegated shared-mailbox rights, not service-principal Outlook auth; deny before content; trace actual item/result |
| Intake/save -> file and row references | Original intake/save design; SharePoint `CreateFile`, Dataverse `CreateRecord`/`UpdateOnlyRecord` | Approved test-store writes; atomic intake claim first; retain partial file/row IDs and reconcile unknown writes |
| Attachment -> readable source text | Outlook `GetAttachment_V2` plus verified adapter | Authorized parent message; unsupported -> `unsupported_input`, malformed -> `failed`; no OCR/page guarantees |
| Reference lookup -> matched records/rule findings | Dataverse `GetItem`/bounded `ListRecords`; deterministic checks in form workflow | Read-only approved tables; missing/conflict -> `needs_review`, outage -> `unavailable`; record sources/rule results |
| Form generation -> form/exception and version | `GeneratePaymentFormFlow`: template, SharePoint `CreateFile`, controlled Dataverse update | Scoped write role; atomic business-key guard and version check; exception cannot start approval; verify returned state |
| Status -> recorded package result | `ReadInvoiceStatus`: Dataverse `GetItem`/fixed `ListRecords` | Authorized read only; no hidden workflow restart; actual IDs/status |
| Approval start -> request ID; separate read -> decision | `ApprovalRequestFlow`: `CreateAnApproval`/`StartAndWaitForAnApproval`; `WaitForAnApproval` or recorded row | OFF initially; exact-preview approval and dedicated approver; verify principal/request/version; read never sends |

Preserve `denied`, `unavailable`, `unsupported_input`, `failed`, `duplicate`,
`pending`, `unknown_outcome` and `capability_disabled`. Successful approval reads
return `ok` plus `approved`/`rejected`; neither executes payment. Observe effects
through agent trace and approved flow history, not a new audit platform.

See [architecture](../2.Architecture.md) for the full process and
[workflow controls](README.md#workflow-controls) for version, duplicate and approval
rules. [Technical references](README.md#technical-references) link the official
documentation. No directory-profile connector is needed for the current read/package
path; any later approver-resolution integration needs its own agreed authority rules.

</details>
