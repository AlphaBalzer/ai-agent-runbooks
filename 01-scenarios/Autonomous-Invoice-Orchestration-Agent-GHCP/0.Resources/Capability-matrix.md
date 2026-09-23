# Components - Autonomous Invoice Orchestration Agent (GHCP)

Keep the original process; add one review skill to a GHCP agent.

| Part | What it does | GHCP change |
|---|---|---|
| Email intake and save flows | Receive the PDF, save it to SharePoint and create the transaction. | Pass the transaction to the GHCP agent. |
| ParseInvoiceFlow | Extract PDF fields, apply the agreed reference checks and return the result. | No new extraction engine required. |
| [invoice-review](../Skills/invoice-review/SKILL.md) | Review returned facts and findings; explain missing or conflicting information. | One new read-only skill, no extra tool required. |
| GeneratePaymentFormFlow | Create and save the HTML payment request from eligible invoice data. | Keep the original approach and controls. |
| ApprovalRequestFlow | Obtain the authorized manager decision, record it and notify agreed recipients. | Keep the existing human-owned workflow. |

## Before connecting the agent

Confirm these actual flow contracts in the target environment; their names alone are not proof
that the tools exist or are compatible:

| Flow | Input | Result the agent needs |
|---|---|---|
| ParseInvoiceFlow | The intake transaction's RowId. | Explicit status, invoice fields, available source references and accounting-reference/check findings. |
| GeneratePaymentFormFlow | The same reviewed transaction reference; any version field required by the existing flow. | Actual status and saved form link, or an explicit failure/duplicate outcome. |
| ApprovalRequestFlow | The eligible reviewed request and required authorization. | Actual request/state reference; pending until the human decision is recorded. |

Bind the actual field names. Do not force the earlier pilot's 15-field response or record-ID
allow-list into these flows. If extraction returns only a status, expose its already-saved
details through the existing flow before expecting the review skill to inspect them.

## Skill boundary

`invoice-review` consumes the parsing workflow's results. It neither calls the parsing flow
again nor creates a form or approval. Missing references stop for review; the skill does not
invent a new lookup tool. The orchestrating agent requests the subsequent permitted workflows.

Preserve workflow-enforced access, financial checks, duplicate handling, source-version checks
and human approval. Simpler instructions do not authorize bypassing them.

## Readiness

Only the instruction and skill files are supplied for this simplified variant. The original
PDF workflow bindings and end-to-end behavior still need implementation and demonstration.
See [delivery status](README.md#delivery-status). The [earlier pilot](Archive/README.txt) and its
two runtime skills are preserved separately and are not deployed by this guide.
