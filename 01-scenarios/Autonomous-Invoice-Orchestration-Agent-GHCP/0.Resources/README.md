# Resources - Autonomous Invoice Orchestration Agent (GHCP)

## Start here

Use the [main runbook](../3.Runbook.md) for the **original PDF process with a small GHCP review
step**. Keep the original intake, save, extraction, HTML form and approval stages.

| Resource | When to use it |
|---|---|
| [Original runbook and screenshots](../../Autonomous-Invoice-Orchestration-Agent/3.Runbook.md) | Supporting-flow design and configuration examples. |
| [Original sample PDF](../../Autonomous-Invoice-Orchestration-Agent/0.Resources/Sample_Invoice.pdf) | First digital-PDF example, after permitted setup. |
| [Small GHCP addition](../3.Runbook.md#1-create-the-ghcp-agent) | Proposed agent instructions and one review-skill draft. |
| [Earlier illustrated test-build guide](https://github.com/AlphaBalzer/ai-agent-runbooks/blob/77a9c27c9e85508d80bf3e6f618b08b8953f35a1/01-scenarios/Autonomous-Invoice-Orchestration-Agent-GHCP/3.Runbook.md) | Historical snapshot of the more involved text-only build, not the recommended PDF path. |

You do not need to import or understand the reconstruction JSON to follow the main story.
Those files describe the earlier controlled text pilot; they are not GHCP requirements or a
deployable solution package. Its existing workflows, skills, screenshots and raw results are
preserved. Do not attach the old snapshot-specific instructions to the proposed PDF flow.

## Delivery status

**23 September 2026: simplifying the build, not claiming completion.**

| Area | Actual position |
|---|---|
| **Recommended path** | Original PDF intake/extraction/form/approval process with a small GHCP review skill. This simplified variant has not been built or demonstrated end to end. |
| **Existing test agent** | Published without added channels. Actual workflow Agent-node calls reached its configured source, reference and form tools. This does not prove the original Preview issue is repaired. |
| **Text invoice to HTML** | One approved synthetic text invoice was received, manually ingested and processed by the published agent into a saved HTML form. The actual file rendered in SharePoint; JSON remained in Dataverse. |
| **Sequential replay** | Returned the same HTML package without a second file or package row. Not a concurrency or broad reliability result. |
| **Remaining defect** | Replay response shortened long attachment citation IDs. Stored package identity was correct; exact-citation acceptance is incomplete. |
| **PDF extraction / approval / automatic intake** | Not demonstrated for the GHCP variant. Existing approval notifications remain off; payment/posting are excluded. |

The repository's JSON definitions and result record describe the earlier September 21
snapshot, not an export of the later live HTML changes. The dated notes below are retained
as historical evidence; their old "unpublished" and "JSON only" statements are not current
deployment claims. No previous failed or unrun case is silently marked passed.

**Next delivery work:** confirm the original PDF extraction/tool contracts, implement the
small review skill against those outputs, then demonstrate the PDF-to-form-to-real-approval
sequence. Do not continue extending the text-fixture implementation by default.

<details>
<summary>Earlier text-pilot implementation and technical references (optional)</summary>

The sections below preserve the existing technical material and links. They are not mandatory
setup steps for the simplified path. The field sheets exactly describe the supplied older
definitions, not the proposed PDF workflows or later live HTML amendments.

## Screenshot provenance

Captured on 23 September 2026 from the existing isolated configuration. No agent prompts,
workflow executions, saves, publication, skill uploads, permission changes or notifications
were performed to create these illustrations. Browser/account chrome is excluded; environment
and site values are masked. Crops remove empty space, not failed steps or error outcomes.

| Image | What it actually shows |
|---|---|
| [Active keys](Images/00-active-keys.png) | Existing separate Unique Intake and Unique Invoice indexes in Active state; not a concurrency test. |
| [Agent Build](Images/01-agent-build.png) | Existing draft agent, two skills and three attached tools; not successful agent execution. |
| [Upload a skill](Images/02-upload-skill.png) | Upload dialog opened without uploading or replacing a skill. |
| [Save source](Images/03-save-source.png) | Existing SharePoint Create file settings; site address hidden. |
| [Reader query](Images/04-reader-query.png) | Existing selected-environment Dataverse query; environment hidden. |
| [Reader input](Images/05-reader-input.png) | Attached tool's required source-record input. |
| [Reader outputs](Images/06-reader-outputs.png) | Existing status/source_id/record_json/version contract. |
| [Generator inputs](Images/07-generator-inputs.png) | Existing record_id/expected_version inputs; permission setting is not an approval decision. |
| [Financial checks](Images/08-recorded-financial-checks.png) | Outputs of the recorded normal PO component run from 21 September, not a new agent run. |

The pilot resource names in images are intentionally retained; changing the documentation title
does not rename deployed resources. Screenshots are not instructions to copy the test model or
broaden tool permissions. The current designer may mark a view dirty merely after opening a
node; discard that view rather than saving during inspection.

## Earlier component evidence - 21 September

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

<!-- BEGIN GENERATED FINANCE FIELD SHEETS -->
## Copyable workflow fields

These expandable field sheets translate the four existing reconstruction references into
designer fields. They do not add missing behavior or turn the JSON into an importable solution.
Build in the order in the [runbook](../3.Runbook.md). Read the branch location and **Run after**
for every action; canvas proximity alone does not set failure handling.

- Select your connection and environment; replace every `__PLACEHOLDER__` before use.
- Map the `cr090_` names to your actual column logical names and entity set name.
- Expression-editor values below omit the JSON definition's leading `@`. Do not paste
  an expression as literal text or paste the whole definition into a single node.
- Rename actions before adding expressions that reference them. Check internal names
  against the definition if the designer normalizes spaces or adds a numeric suffix.
- For **Select**, `json('[{}]')` means one empty object so the map produces one result.
  It does not read a table. Output values remain the types returned by each expression.
- A branch with no actions is deliberately recorded as empty, not an invented error handler.
  The [delivery limitations](#delivery-status) still apply.

### Intake fields

Source: [Invoice-intake.definition.json](Invoice-intake.definition.json).

#### Trigger inputs

Select **When an agent calls the workflow**; add required Text inputs in this order:

| Display name | Internal key | Description |
|---|---|---|
| `messageId` | `text` | Approved received invoice ID. Claims one test record and saves its attachment to the fixed Invoice SharePoint folder. Never starts approval or payment. |

#### Initialize_intake_result

<details>
<summary>Variable / Initialize variable - open exact fields</summary>

**Location:** `Initialize_intake_result`. Use display name **Initialize intake result**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**Variable name** - Literal / structured value

```text
intake_result
```

**Variable type** - Literal / structured value

```text
Object
```

**Initial value** - Expression editor

```text
json('{"record_id":"","source_file_url":"","source_file_id":"","created":false,"status":"capability_disabled","record_state":"not_started","reconciliation":"not_run","error_code":"scope_or_input_not_allowed"}')
```

</details>

#### Get_email

<details>
<summary>Connector / Office 365 Outlook / Get email (V2) - open exact fields</summary>

**Location:** `Get_email`. Use display name **Get email**.

**Run after:** `Initialize_intake_result`: Succeeded.

**Native operation:** `GetEmailV2`. Select your approved connection; do not copy a connection ID.

**Include attachments** - Literal / structured value

```text
true
```

**Message Id** - Expression editor

```text
triggerBody()?['text']
```

**Original Mailbox Address** - Literal / structured value

```text
__TEST_SHARED_MAILBOX__
```

**Fetch sensitivity label metadata** - Literal / structured value

```text
true
```

**Extract sensitivity label** - Literal / structured value

```text
true
```

</details>

#### Select

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Select`. Use display name **Select**.

**Run after:** `Get_email`: Succeeded.

**From** - Expression editor

```text
if(equals(outputs('Get_email')?['body/hasAttachments'], true), outputs('Get_email')?['body/attachments'], json('[]'))
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**source_id** - Expression editor

```text
item()?['id']
```

**name** - Expression editor

```text
item()?['name']
```

**status** - Expression editor

```text
if(and(lessOrEquals(length(outputs('Get_email')?['body/attachments']), 5), endsWith(toLower(coalesce(item()?['name'], '')), '.txt'), or(startsWith(toLower(coalesce(item()?['contentType'], '')), 'text/plain'), equals(toLower(coalesce(item()?['contentType'], '')), 'application/octet-stream')), lessOrEquals(coalesce(item()?['size'], 65537), 65536), not(empty(item()?['contentBytes'])), not(equals(item()?['isInline'], true))), 'ok', 'unsupported_input')
```

**text** - Expression editor

```text
if(and(lessOrEquals(length(outputs('Get_email')?['body/attachments']), 5), endsWith(toLower(coalesce(item()?['name'], '')), '.txt'), or(startsWith(toLower(coalesce(item()?['contentType'], '')), 'text/plain'), equals(toLower(coalesce(item()?['contentType'], '')), 'application/octet-stream')), lessOrEquals(coalesce(item()?['size'], 65537), 65536), not(empty(item()?['contentBytes'])), not(equals(item()?['isInline'], true))), base64ToString(item()?['contentBytes']), '')
```

</details>

#### Allowed_invoice_intake

<details>
<summary>If/Else - open exact fields</summary>

**Location:** `Allowed_invoice_intake`. Use display name **Allowed invoice intake**.

**Run after:** `Select`: Succeeded.

**Condition - left value** - Expression editor

```text
if(equals(length(coalesce(outputs('Get_email')?['body/attachments'],json('[]'))),1),if(and(contains(json('["__SEED_NORMAL_MESSAGE_ID__","__SEED_MISSING_MESSAGE_ID__","__SEED_NOPO_MESSAGE_ID__","__SEED_CONFLICT_MESSAGE_ID__","__SEED_MALICIOUS_MESSAGE_ID__","__SEED_DUPLICATE_MESSAGE_ID__","__SEED_UNSUPPORTED_MESSAGE_ID__"]'),triggerBody()?['text']),not(empty(triggerBody()?['text'])),lessOrEquals(length(triggerBody()?['text']),287),equals(outputs('Get_email')?['body/id'],triggerBody()?['text']),lessOrEquals(coalesce(first(coalesce(outputs('Get_email')?['body/attachments'],json('[]')))?['size'],65537),65536),not(equals(first(coalesce(outputs('Get_email')?['body/attachments'],json('[]')))?['isInline'],true)),not(empty(first(coalesce(outputs('Get_email')?['body/attachments'],json('[]')))?['contentBytes']))),'enabled','disabled'),'disabled')
```

**Condition - operator** - Literal / structured value

```text
is equal to
```

**Condition - right value** - Literal / structured value

```text
enabled
```

Actions below are in **True / If**. **False / Else is empty in this reference**; the initialized result is returned. This is not proof of comprehensive failure classification.

</details>

#### Claim_intake

<details>
<summary>Connector / Microsoft Dataverse / Add a new row to selected environment - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Claim_intake`. Use display name **Claim intake**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**Native operation:** `CreateRecordWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**cr090_intakekey** - Expression editor

```text
concat('ghcp-invoice|',triggerBody()?['text'])
```

**cr090_reviewstate** - Literal / structured value

```text
intake_claimed
```

</details>

#### Save_source

<details>
<summary>Connector / SharePoint / Create file - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Save_source`. Use display name **Save source**.

**Run after:** `Claim_intake`: Succeeded.

**Native operation:** `CreateFile`. Select your approved connection; do not copy a connection ID.

**Site address** - Literal / structured value

```text
__INVOICE_SITE_URL__
```

**Folder path** - Literal / structured value

```text
/Shared Documents/Incoming
```

**File name** - Expression editor

```text
concat(outputs('Claim_intake')?['body/cr090_ghcpinvoicereviewid'],if(equals(first(body('Select'))?['status'],'ok'),'.txt','.bin'))
```

**File content** - Expression editor

```text
base64ToBinary(first(outputs('Get_email')?['body/attachments'])?['contentBytes'])
```

</details>

#### Source_snapshot

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Source_snapshot`. Use display name **Source snapshot**.

**Run after:** `Save_source`: Succeeded.

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**schema_version** - Literal / structured value

```text
1
```

**approval_state** - Literal / structured value

```text
not_requested
```

**record_version** - Expression editor

```text
int('1')
```

**record_id** - Expression editor

```text
outputs('Claim_intake')?['body/cr090_ghcpinvoicereviewid']
```

**source_id** - Expression editor

```text
outputs('Get_email')?['body/id']
```

**subject** - Expression editor

```text
outputs('Get_email')?['body/subject']
```

**body** - Expression editor

```text
outputs('Get_email')?['body/body']
```

**sender** - Expression editor

```text
outputs('Get_email')?['body/from']
```

**attachments** - Expression editor

```text
body('Select')
```

**source_file_id** - Expression editor

```text
outputs('Save_source')?['body/Id']
```

**source_file_path** - Expression editor

```text
outputs('Save_source')?['body/Path']
```

</details>

#### Record_saved_source

<details>
<summary>Connector / Microsoft Dataverse / Update a row in selected environment - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Record_saved_source`. Use display name **Record saved source**.

**Run after:** `Source_snapshot`: Succeeded.

**Native operation:** `UpdateOnlyRecordWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Row ID** - Expression editor

```text
outputs('Claim_intake')?['body/cr090_ghcpinvoicereviewid']
```

**cr090_reviewstate** - Literal / structured value

```text
source_saved
```

**cr090_sourcefileurl** - Expression editor

```text
concat('__INVOICE_SITE_URL__',replace(uriComponent(outputs('Save_source')?['body/Path']),'%2F','/'))
```

**cr090_reviewpayload** - Expression editor

```text
string(first(body('Source_snapshot')))
```

</details>

#### Reconcile_intake

<details>
<summary>Connector / Microsoft Dataverse / List rows from selected environment - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Reconcile_intake`. Use display name **Reconcile intake**.

**Run after:** `Record_saved_source`: Succeeded, Failed, TimedOut, Skipped.

**Native operation:** `ListRecordsWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Select columns** - Literal / structured value

```text
cr090_ghcpinvoicereviewid,cr090_intakekey,cr090_reviewstate,cr090_sourcefileurl,cr090_reviewpayload,versionnumber
```

**Filter rows** - Expression editor

```text
concat('cr090_intakekey eq ''ghcp-invoice|',replace(triggerBody()?['text'],'''',''''''),'''')
```

**Row count** - Literal / structured value

```text
2
```

</details>

#### Intake_outcome

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Intake_outcome`. Use display name **Intake outcome**.

**Run after:** `Reconcile_intake`: Succeeded, Failed, TimedOut, Skipped.

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**record_id** - Expression editor

```text
coalesce(outputs('Claim_intake')?['body/cr090_ghcpinvoicereviewid'],if(equals(length(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]'))),1),first(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]')))?['cr090_ghcpinvoicereviewid'],''),'')
```

**source_file_url** - Expression editor

```text
coalesce(if(equals(length(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]'))),1),first(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]')))?['cr090_sourcefileurl'],null),if(equals(actions('Save_source')?['status'],'Succeeded'),concat('__INVOICE_SITE_URL__',replace(uriComponent(outputs('Save_source')?['body/Path']),'%2F','/')),''),'')
```

**source_file_id** - Expression editor

```text
coalesce(outputs('Save_source')?['body/Id'],'')
```

**created** - Expression editor

```text
equals(actions('Claim_intake')?['status'],'Succeeded')
```

**status** - Expression editor

```text
if(and(equals(actions('Reconcile_intake')?['status'],'Succeeded'),if(equals(length(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]'))),1),equals(first(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]')))?['cr090_reviewstate'],'source_saved'),false)),if(equals(actions('Record_saved_source')?['status'],'Succeeded'),if(equals(first(body('Select'))?['status'],'ok'),'ok','unsupported_input'),'duplicate'),if(or(equals(outputs('Claim_intake')?['statusCode'],401),equals(outputs('Claim_intake')?['statusCode'],403)),'denied',if(or(and(equals(actions('Save_source')?['status'],'Failed'),greaterOrEquals(coalesce(outputs('Save_source')?['statusCode'],0),400),less(coalesce(outputs('Save_source')?['statusCode'],0),500)),and(equals(actions('Record_saved_source')?['status'],'Failed'),greaterOrEquals(coalesce(outputs('Record_saved_source')?['statusCode'],0),400),less(coalesce(outputs('Record_saved_source')?['statusCode'],0),500))),'failed','unknown_outcome')))
```

**error_code** - Expression editor

```text
concat('claim=',coalesce(actions('Claim_intake')?['status'],'not_run'),';file=',coalesce(actions('Save_source')?['status'],'not_run'),';record=',coalesce(actions('Record_saved_source')?['status'],'not_run'),';reconcile=',coalesce(actions('Reconcile_intake')?['status'],'not_run'))
```

**record_state** - Expression editor

```text
coalesce(if(equals(length(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]'))),1),first(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]')))?['cr090_reviewstate'],null),if(equals(actions('Claim_intake')?['status'],'Succeeded'),'intake_claimed','unknown'),'unknown')
```

**reconciliation** - Expression editor

```text
if(equals(actions('Reconcile_intake')?['status'],'Succeeded'),if(equals(length(coalesce(outputs('Reconcile_intake')?['body/value'],json('[]'))),1),'confirmed','not_reconciled'),'unavailable')
```

</details>

#### Set_intake_result

<details>
<summary>Variable / Set variable - open exact fields</summary>

**Location:** `Allowed_invoice_intake > True > Set_intake_result`. Use display name **Set intake result**.

**Run after:** `Intake_outcome`: Succeeded.

**Variable name** - Literal / structured value

```text
intake_result
```

**Value** - Expression editor

```text
first(body('Intake_outcome'))
```

</details>

#### Respond_to_the_agent

<details>
<summary>Function / Respond to the agent - open exact fields</summary>

**Location:** `Respond_to_the_agent`. Use display name **Respond to the agent**.

**Run after:** `Allowed_invoice_intake`: Succeeded, Failed, TimedOut, Skipped.

Create Text outputs in the following order. The internal keys are shown for matching expressions.

**Output record_id (internal text)** - Expression editor

```text
variables('intake_result')?['record_id']
```

**Output source_id (internal text_1)** - Expression editor

```text
if(equals(actions('Get_email')?['status'],'Succeeded'),outputs('Get_email')?['body/id'],'')
```

**Output source_file_url (internal text_2)** - Expression editor

```text
variables('intake_result')?['source_file_url']
```

**Output source_file_id (internal text_3)** - Expression editor

```text
variables('intake_result')?['source_file_id']
```

**Output created (internal boolean)** - Expression editor

```text
variables('intake_result')?['created']
```

**Output status (internal text_4)** - Expression editor

```text
if(not(equals(actions('Get_email')?['status'],'Succeeded')),if(or(equals(outputs('Get_email')?['statusCode'],401),equals(outputs('Get_email')?['statusCode'],403)),'denied',if(or(equals(actions('Get_email')?['status'],'TimedOut'),equals(outputs('Get_email')?['statusCode'],429),greaterOrEquals(coalesce(outputs('Get_email')?['statusCode'],0),500)),'unavailable','failed')),if(not(equals(actions('Select')?['status'],'Succeeded')),'failed',if(and(equals(variables('intake_result')?['status'],'capability_disabled'),not(equals(actions('Allowed_invoice_intake')?['status'],'Succeeded'))),'unknown_outcome',variables('intake_result')?['status'])))
```

**Output error_code (internal text_5)** - Expression editor

```text
variables('intake_result')?['error_code']
```

**Output record_state (internal text_6)** - Expression editor

```text
variables('intake_result')?['record_state']
```

**Output reconciliation (internal text_7)** - Expression editor

```text
variables('intake_result')?['reconciliation']
```

</details>

### Reader fields

Source: [Invoice-record-read.definition.json](Invoice-record-read.definition.json).

#### Trigger inputs

Select **When an agent calls the workflow**; add required Text inputs in this order:

| Display name | Internal key | Description |
|---|---|---|
| `record_id` | `text` | Existing approved Invoice pilot record ID. Reads its saved source snapshot and state only; never ingests mail, creates files, updates rows or starts approval. This is a stored snapshot, not a fresh mailbox read. |

#### Read_approved_record

<details>
<summary>Connector / Microsoft Dataverse / List rows from selected environment - open exact fields</summary>

**Location:** `Read_approved_record`. Use display name **Read approved record**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**Native operation:** `ListRecordsWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Select columns** - Literal / structured value

```text
cr090_ghcpinvoicereviewid,cr090_intakekey,cr090_invoicekey,cr090_reviewstate,cr090_sourcefileurl,cr090_packagefileurl,cr090_reviewpayload,versionnumber
```

**Filter rows** - Expression editor

```text
concat('cr090_ghcpinvoicereviewid eq ',if(equals(triggerBody()?['text'],'__NORMAL_SOURCE_RECORD_ID__'),triggerBody()?['text'],'__DENIED_ROW_ID__'))
```

**Row count** - Literal / structured value

```text
2
```

</details>

#### Respond_to_the_agent

<details>
<summary>Function / Respond to the agent - open exact fields</summary>

**Location:** `Respond_to_the_agent`. Use display name **Respond to the agent**.

**Run after:** `Read_approved_record`: Succeeded, Failed, TimedOut, Skipped.

Create Text outputs in the following order. The internal keys are shown for matching expressions.

**Output status (internal text)** - Expression editor

```text
if(not(equals(triggerBody()?['text'],'__NORMAL_SOURCE_RECORD_ID__')),'denied',if(equals(actions('Read_approved_record')?['status'],'Succeeded'),if(equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1),'ok',if(equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),0),'not_found','failed')),if(or(equals(outputs('Read_approved_record')?['statusCode'],401),equals(outputs('Read_approved_record')?['statusCode'],403)),'denied',if(or(equals(actions('Read_approved_record')?['status'],'TimedOut'),equals(outputs('Read_approved_record')?['statusCode'],429),greaterOrEquals(coalesce(outputs('Read_approved_record')?['statusCode'],0),500)),'unavailable','failed'))))
```

**Output source_id (internal text_1)** - Expression editor

```text
if(and(equals(actions('Read_approved_record')?['status'],'Succeeded'),equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1)),first(outputs('Read_approved_record')?['body/value'])?['cr090_ghcpinvoicereviewid'],'')
```

**Output record_json (internal text_2)** - Expression editor

```text
if(and(equals(actions('Read_approved_record')?['status'],'Succeeded'),equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1)),string(first(outputs('Read_approved_record')?['body/value'])),'')
```

**Output version (internal text_3)** - Expression editor

```text
if(and(equals(actions('Read_approved_record')?['status'],'Succeeded'),equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1)),string(first(outputs('Read_approved_record')?['body/value'])?['versionnumber']),'')
```

</details>

### Reference fields

Source: [Finance-reference.definition.json](Finance-reference.definition.json).

#### Trigger inputs

Select **When an agent calls the workflow**; add required Text inputs in this order:

| Display name | Internal key | Description |
|---|---|---|
| `reference_id` | `text` | Exact synthetic finance reference ID ref-vendors, ref-po-7788, ref-receipt-7788, ref-gl-6100, ref-cc-204 or ref-nopo-policy; bundle-po returns vendor/PO/receipt/GL/CC entries, bundle-nopo returns vendor/no-PO policy. Not production ERP or policy. Read-only; unknown ID returns not_found. |

#### Respond_to_the_agent

<details>
<summary>Function / Respond to the agent - open exact fields</summary>

**Location:** `Respond_to_the_agent`. Use display name **Respond to the agent**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

Create Text outputs in the following order. The internal keys are shown for matching expressions.

**Output status (internal text)** - Expression editor

```text
if(contains(createArray('bundle-po','bundle-nopo','ref-vendors','ref-po-7788','ref-receipt-7788','ref-gl-6100','ref-cc-204','ref-nopo-policy'),toLower(trim(coalesce(triggerBody()?['text'],'')))),'ok','not_found')
```

**Output source_id (internal text_1)** - Expression editor

```text
toLower(trim(coalesce(triggerBody()?['text'],'')))
```

**Output text (internal text_2)** - Expression editor

```text
if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-nopo-policy'),'[{"source_id":"ref-nopo-policy","text":"NOPO-PROF-SERVICES-LOW approved for vendor VEND-NOPO-SYN, GL 6200, cost centre CC-310, currency AUD; advisory invoices up to AUD 500.00 require no PO or due date but always require finance review."}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-cc-204'),'[{"source_id":"ref-cc-204","text":"Cost centre CC-204 approved for synthetic finance operations"}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-gl-6100'),'[{"source_id":"ref-gl-6100","text":"GL 6100 approved for synthetic services expense"}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-receipt-7788'),'[{"source_id":"ref-receipt-7788","text":"Receipt RCPT-7788-1 for PO PO-7788-SYN line 1 received quantity 2"}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-po-7788'),'[{"source_id":"ref-po-7788","text":"PO PO-7788-SYN vendor VEND-ACME-SYN approved line Synthetic support hours quantity 2 unit price 50.00 line total 100.00 currency AUD"}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'ref-vendors'),'[{"source_id":"ref-vendors","text":"ACME Supplies Synthetic Ltd maps to approved vendor VEND-ACME-SYN. NoPO Advisory Synthetic Pty Ltd maps to approved vendor VEND-NOPO-SYN. Legal entity SYN-ENTITY uses AUD. PO-7788-SYN uses GL 6100 and cost centre CC-204."}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'bundle-nopo'),'[{"source_id":"ref-vendors","text":"ACME Supplies Synthetic Ltd maps to approved vendor VEND-ACME-SYN. NoPO Advisory Synthetic Pty Ltd maps to approved vendor VEND-NOPO-SYN. Legal entity SYN-ENTITY uses AUD. PO-7788-SYN uses GL 6100 and cost centre CC-204."},{"source_id":"ref-nopo-policy","text":"NOPO-PROF-SERVICES-LOW approved for vendor VEND-NOPO-SYN, GL 6200, cost centre CC-310, currency AUD; advisory invoices up to AUD 500.00 require no PO or due date but always require finance review."}]',if(equals(toLower(trim(coalesce(triggerBody()?['text'],''))),'bundle-po'),'[{"source_id":"ref-vendors","text":"ACME Supplies Synthetic Ltd maps to approved vendor VEND-ACME-SYN. NoPO Advisory Synthetic Pty Ltd maps to approved vendor VEND-NOPO-SYN. Legal entity SYN-ENTITY uses AUD. PO-7788-SYN uses GL 6100 and cost centre CC-204."},{"source_id":"ref-po-7788","text":"PO PO-7788-SYN vendor VEND-ACME-SYN approved line Synthetic support hours quantity 2 unit price 50.00 line total 100.00 currency AUD"},{"source_id":"ref-receipt-7788","text":"Receipt RCPT-7788-1 for PO PO-7788-SYN line 1 received quantity 2"},{"source_id":"ref-gl-6100","text":"GL 6100 approved for synthetic services expense"},{"source_id":"ref-cc-204","text":"Cost centre CC-204 approved for synthetic finance operations"}]','[]'))))))))
```

**Output version (internal text_3)** - Literal / structured value

```text
synthetic-finance-catalogue-2026-09-21; not production ERP/policy
```

</details>

### Generator fields

Source: [Generate-review-package.definition.json](Generate-review-package.definition.json).

#### Trigger inputs

Select **When an agent calls the workflow**; add required Text inputs in this order:

| Display name | Internal key | Description |
|---|---|---|
| `record_id` | `text` | Approved Invoice intake record ID. Explicit composite action: deterministic validation, unique package claim, fixed SharePoint review file and package-state row update. No approval start/payment. |
| `expected_version` | `text_1` | Exact Dataverse version returned by the latest approved record read. A mismatch stops generation for renewed review. |

#### Initialize_package_result

<details>
<summary>Variable / Initialize variable - open exact fields</summary>

**Location:** `Initialize_package_result`. Use display name **Initialize package result**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**Variable name** - Literal / structured value

```text
package_result
```

**Variable type** - Literal / structured value

```text
Object
```

**Initial value** - Expression editor

```text
json('{"status":"needs_review","record_id":"","package_file_url":"","reason":"Source version, evidence or supported scope requires review","approval_state":"not_requested"}')
```

</details>

#### Read_approved_record

<details>
<summary>Connector / Microsoft Dataverse / List rows from selected environment - open exact fields</summary>

**Location:** `Read_approved_record`. Use display name **Read approved record**.

**Run after:** `Initialize_package_result`: Succeeded.

**Native operation:** `ListRecordsWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Select columns** - Literal / structured value

```text
cr090_ghcpinvoicereviewid,cr090_intakekey,cr090_invoicekey,cr090_reviewstate,cr090_sourcefileurl,cr090_packagefileurl,cr090_reviewpayload,versionnumber
```

**Filter rows** - Expression editor

```text
concat('cr090_ghcpinvoicereviewid eq ',if(equals(triggerBody()?['text'],'__NORMAL_SOURCE_RECORD_ID__'),triggerBody()?['text'],'__DENIED_ROW_ID__'))
```

**Row count** - Literal / structured value

```text
2
```

</details>

#### Source_current

<details>
<summary>If/Else - open exact fields</summary>

**Location:** `Source_current`. Use display name **Source current**.

**Run after:** `Read_approved_record`: Succeeded.

**Condition - left value** - Expression editor

```text
if(equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1),if(and(equals(string(first(outputs('Read_approved_record')?['body/value'])?['versionnumber']),triggerBody()?['text_1']),equals(first(outputs('Read_approved_record')?['body/value'])?['cr090_reviewstate'],'source_saved'),not(empty(first(outputs('Read_approved_record')?['body/value'])?['cr090_reviewpayload']))),'yes','no'),'no')
```

**Condition - operator** - Literal / structured value

```text
is equal to
```

**Condition - right value** - Literal / structured value

```text
yes
```

Actions below are in **True / If**. **False / Else is empty in this reference**; the initialized result is returned. This is not proof of comprehensive failure classification.

</details>

#### Stored_snapshot

<details>
<summary>Function / Compose - open exact fields</summary>

**Location:** `Source_current > True > Stored_snapshot`. Use display name **Stored snapshot**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**Inputs** - Expression editor

```text
json(first(outputs('Read_approved_record')?['body/value'])?['cr090_reviewpayload'])
```

</details>

#### Text_source_supported

<details>
<summary>If/Else - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported`. Use display name **Text source supported**.

**Run after:** `Stored_snapshot`: Succeeded.

**Condition - left value** - Expression editor

```text
if(equals(length(coalesce(outputs('Stored_snapshot')?['attachments'],json('[]'))),1),if(and(equals(first(coalesce(outputs('Stored_snapshot')?['attachments'],json('[]')))?['status'],'ok'),not(empty(first(coalesce(outputs('Stored_snapshot')?['attachments'],json('[]')))?['text'])),lessOrEquals(length(first(coalesce(outputs('Stored_snapshot')?['attachments'],json('[]')))?['text']),65536)),'yes','no'),'no')
```

**Condition - operator** - Literal / structured value

```text
is equal to
```

**Condition - right value** - Literal / structured value

```text
yes
```

Actions below are in **True / If**. **False / Else is empty in this reference**; the initialized result is returned. This is not proof of comprehensive failure classification.

</details>

#### Invoice_fields

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Invoice_fields`. Use display name **Invoice fields**.

**Run after:** first action in this branch (no explicit predecessor in the reference).

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**supplier** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Supplier: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Supplier: '))),decodeUriComponent('%0A')))),'')
```

**invoice_number** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Invoice Number: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Invoice Number: '))),decodeUriComponent('%0A')))),'')
```

**invoice_date** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Invoice Date: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Invoice Date: '))),decodeUriComponent('%0A')))),'')
```

**due_date** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Due Date: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Due Date: '))),decodeUriComponent('%0A')))),'')
```

**po** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'PO: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'PO: '))),decodeUriComponent('%0A')))),'')
```

**line** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Line 1: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Line 1: '))),decodeUriComponent('%0A')))),'')
```

**services** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Services: '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Services: '))),decodeUriComponent('%0A')))),'')
```

**subtotal_text** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Subtotal AUD '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Subtotal AUD '))),decodeUriComponent('%0A')))),'')
```

**tax_text** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Tax AUD '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Tax AUD '))),decodeUriComponent('%0A')))),'')
```

**total_text** - Expression editor

```text
if(equals(length(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Total AUD '))),2),trim(first(split(last(split(concat(decodeUriComponent('%0A'),replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')),concat(decodeUriComponent('%0A'),'Total AUD '))),decodeUriComponent('%0A')))),'')
```

**attachment_source_id** - Expression editor

```text
first(outputs('Stored_snapshot')?['attachments'])?['source_id']
```

**source_text** - Expression editor

```text
replace(first(outputs('Stored_snapshot')?['attachments'])?['text'],decodeUriComponent('%0D'),'')
```

</details>

#### Financial_checks

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Financial_checks`. Use display name **Financial checks**.

**Run after:** `Invoice_fields`: Succeeded.

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**vendor_id** - Expression editor

```text
if(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),'VEND-ACME-SYN',if(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),'VEND-NOPO-SYN',''))
```

**legal_entity** - Literal / structured value

```text
SYN-ENTITY
```

**currency** - Literal / structured value

```text
AUD
```

**path** - Expression editor

```text
if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),'po',if(and(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),empty(first(body('Invoice_fields'))?['po']),equals(first(body('Invoice_fields'))?['services'],'Advisory hours')),'nopo','exception'))
```

**subtotal_cents** - Expression editor

```text
if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),10000,if(and(not(empty(first(body('Invoice_fields'))?['subtotal_text'])),equals(length(split(first(body('Invoice_fields'))?['subtotal_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['subtotal_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'-')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'+')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['subtotal_text']),'e'))),int(replace(first(body('Invoice_fields'))?['subtotal_text'],'.','')),-1))
```

**tax_cents** - Expression editor

```text
if(and(not(empty(first(body('Invoice_fields'))?['tax_text'])),equals(length(split(first(body('Invoice_fields'))?['tax_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['tax_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['tax_text'],'-')),not(contains(first(body('Invoice_fields'))?['tax_text'],'+')),not(contains(first(body('Invoice_fields'))?['tax_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['tax_text']),'e'))),int(replace(first(body('Invoice_fields'))?['tax_text'],'.','')),-1)
```

**total_cents** - Expression editor

```text
if(and(not(empty(first(body('Invoice_fields'))?['total_text'])),equals(length(split(first(body('Invoice_fields'))?['total_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['total_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['total_text'],'-')),not(contains(first(body('Invoice_fields'))?['total_text'],'+')),not(contains(first(body('Invoice_fields'))?['total_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['total_text']),'e'))),int(replace(first(body('Invoice_fields'))?['total_text'],'.','')),-1)
```

**identity_complete** - Expression editor

```text
and(not(empty(if(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),'VEND-ACME-SYN',if(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),'VEND-NOPO-SYN','')))),not(empty(first(body('Invoice_fields'))?['invoice_number'])),lessOrEquals(length(first(body('Invoice_fields'))?['invoice_number']),64),not(empty(first(body('Invoice_fields'))?['invoice_date'])))
```

**terms_supported** - Expression editor

```text
or(and(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),not(empty(first(body('Invoice_fields'))?['due_date']))),and(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),empty(first(body('Invoice_fields'))?['po']),equals(first(body('Invoice_fields'))?['services'],'Advisory hours')))
```

**source_flags** - Expression editor

```text
or(contains(toLower(first(body('Invoice_fields'))?['source_text']),'instruction to agent'),contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'instruction to agent'),and(contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'total aud '),not(and(equals(length(split(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'total aud ')),2),contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),concat('total aud ',first(body('Invoice_fields'))?['total_text']))))),and(contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'gl '),not(and(equals(length(split(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'gl ')),2),contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),concat('gl ',if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),'6100','6200')))))),and(contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'cost centre '),not(and(equals(length(split(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),'cost centre ')),2),contains(toLower(coalesce(outputs('Stored_snapshot')?['body'],'')),concat('cost centre ',if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),'cc-204','cc-310')))))))
```

**arithmetic_matches** - Expression editor

```text
and(greaterOrEquals(if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),10000,if(and(not(empty(first(body('Invoice_fields'))?['subtotal_text'])),equals(length(split(first(body('Invoice_fields'))?['subtotal_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['subtotal_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'-')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'+')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['subtotal_text']),'e'))),int(replace(first(body('Invoice_fields'))?['subtotal_text'],'.','')),-1)),0),greaterOrEquals(if(and(not(empty(first(body('Invoice_fields'))?['tax_text'])),equals(length(split(first(body('Invoice_fields'))?['tax_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['tax_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['tax_text'],'-')),not(contains(first(body('Invoice_fields'))?['tax_text'],'+')),not(contains(first(body('Invoice_fields'))?['tax_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['tax_text']),'e'))),int(replace(first(body('Invoice_fields'))?['tax_text'],'.','')),-1),0),greaterOrEquals(if(and(not(empty(first(body('Invoice_fields'))?['total_text'])),equals(length(split(first(body('Invoice_fields'))?['total_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['total_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['total_text'],'-')),not(contains(first(body('Invoice_fields'))?['total_text'],'+')),not(contains(first(body('Invoice_fields'))?['total_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['total_text']),'e'))),int(replace(first(body('Invoice_fields'))?['total_text'],'.','')),-1),0),equals(add(if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),10000,if(and(not(empty(first(body('Invoice_fields'))?['subtotal_text'])),equals(length(split(first(body('Invoice_fields'))?['subtotal_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['subtotal_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'-')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],'+')),not(contains(first(body('Invoice_fields'))?['subtotal_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['subtotal_text']),'e'))),int(replace(first(body('Invoice_fields'))?['subtotal_text'],'.','')),-1)),if(and(not(empty(first(body('Invoice_fields'))?['tax_text'])),equals(length(split(first(body('Invoice_fields'))?['tax_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['tax_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['tax_text'],'-')),not(contains(first(body('Invoice_fields'))?['tax_text'],'+')),not(contains(first(body('Invoice_fields'))?['tax_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['tax_text']),'e'))),int(replace(first(body('Invoice_fields'))?['tax_text'],'.','')),-1)),if(and(not(empty(first(body('Invoice_fields'))?['total_text'])),equals(length(split(first(body('Invoice_fields'))?['total_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['total_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['total_text'],'-')),not(contains(first(body('Invoice_fields'))?['total_text'],'+')),not(contains(first(body('Invoice_fields'))?['total_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['total_text']),'e'))),int(replace(first(body('Invoice_fields'))?['total_text'],'.','')),-1)))
```

**policy_limit** - Expression editor

```text
or(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),and(and(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),empty(first(body('Invoice_fields'))?['po']),equals(first(body('Invoice_fields'))?['services'],'Advisory hours')),lessOrEquals(if(and(not(empty(first(body('Invoice_fields'))?['total_text'])),equals(length(split(first(body('Invoice_fields'))?['total_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['total_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['total_text'],'-')),not(contains(first(body('Invoice_fields'))?['total_text'],'+')),not(contains(first(body('Invoice_fields'))?['total_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['total_text']),'e'))),int(replace(first(body('Invoice_fields'))?['total_text'],'.','')),-1),50000),greaterOrEquals(if(and(not(empty(first(body('Invoice_fields'))?['total_text'])),equals(length(split(first(body('Invoice_fields'))?['total_text'],'.')),2),equals(length(last(split(first(body('Invoice_fields'))?['total_text'],'.'))),2),not(contains(first(body('Invoice_fields'))?['total_text'],'-')),not(contains(first(body('Invoice_fields'))?['total_text'],'+')),not(contains(first(body('Invoice_fields'))?['total_text'],' ')),not(contains(toLower(first(body('Invoice_fields'))?['total_text']),'e'))),int(replace(first(body('Invoice_fields'))?['total_text'],'.','')),-1),0)))
```

**gl** - Expression editor

```text
if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),'6100',if(and(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),empty(first(body('Invoice_fields'))?['po']),equals(first(body('Invoice_fields'))?['services'],'Advisory hours')),'6200',''))
```

**cost_centre** - Expression editor

```text
if(and(equals(first(body('Invoice_fields'))?['supplier'],'ACME Supplies Synthetic Ltd'),equals(first(body('Invoice_fields'))?['po'],'PO-7788-SYN'),equals(first(body('Invoice_fields'))?['line'],'Synthetic support hours Quantity 2 Unit Price 50.00 Line Total 100.00')),'CC-204',if(and(equals(first(body('Invoice_fields'))?['supplier'],'NoPO Advisory Synthetic Pty Ltd'),empty(first(body('Invoice_fields'))?['po']),equals(first(body('Invoice_fields'))?['services'],'Advisory hours')),'CC-310',''))
```

</details>

#### Review_form

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Review_form`. Use display name **Review form**.

**Run after:** `Financial_checks`: Succeeded.

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**template_version** - Literal / structured value

```text
synthetic-finance-review-v1
```

**document_type** - Expression editor

```text
if(and(equals(first(body('Financial_checks'))?['identity_complete'],true),equals(first(body('Financial_checks'))?['terms_supported'],true),equals(first(body('Financial_checks'))?['source_flags'],false),equals(first(body('Financial_checks'))?['arithmetic_matches'],true),equals(first(body('Financial_checks'))?['policy_limit'],true)),'payment_request_review','invoice_exception_review')
```

**status** - Expression editor

```text
if(and(equals(first(body('Financial_checks'))?['identity_complete'],true),equals(first(body('Financial_checks'))?['terms_supported'],true),equals(first(body('Financial_checks'))?['source_flags'],false),equals(first(body('Financial_checks'))?['arithmetic_matches'],true),equals(first(body('Financial_checks'))?['policy_limit'],true)),'ok','needs_review')
```

**source_record_id** - Expression editor

```text
triggerBody()?['text']
```

**source_version** - Expression editor

```text
triggerBody()?['text_1']
```

**invoice_fields** - Expression editor

```text
first(body('Invoice_fields'))
```

**deterministic_checks** - Expression editor

```text
first(body('Financial_checks'))
```

**approved_references** - Expression editor

```text
json('[{"source_id":"ref-vendors","text":"ACME Supplies Synthetic Ltd maps to approved vendor VEND-ACME-SYN. NoPO Advisory Synthetic Pty Ltd maps to approved vendor VEND-NOPO-SYN. Legal entity SYN-ENTITY uses AUD. PO-7788-SYN uses GL 6100 and cost centre CC-204."},{"source_id":"ref-po-7788","text":"PO PO-7788-SYN vendor VEND-ACME-SYN approved line Synthetic support hours quantity 2 unit price 50.00 line total 100.00 currency AUD"},{"source_id":"ref-receipt-7788","text":"Receipt RCPT-7788-1 for PO PO-7788-SYN line 1 received quantity 2"},{"source_id":"ref-gl-6100","text":"GL 6100 approved for synthetic services expense"},{"source_id":"ref-cc-204","text":"Cost centre CC-204 approved for synthetic finance operations"},{"source_id":"ref-nopo-policy","text":"NOPO-PROF-SERVICES-LOW approved for vendor VEND-NOPO-SYN, GL 6200, cost centre CC-310, currency AUD; advisory invoices up to AUD 500.00 require no PO or due date but always require finance review."}]')
```

**source_file_url** - Expression editor

```text
first(outputs('Read_approved_record')?['body/value'])?['cr090_sourcefileurl']
```

**requires_human_review** - Expression editor

```text
true
```

**approval_state** - Literal / structured value

```text
not_requested
```

**limitations** - Literal / structured value

```text
Approved synthetic catalogue and English AUD text format only. Integer-cent checks use the declared source amounts; no tax-law, OCR, ERP, approval or payment validation. Failed or missing fields remain exceptions. Negative numeric sentinel -1 means missing/invalid, never a payable amount.
```

</details>

#### Claim_package

<details>
<summary>Connector / Microsoft Dataverse / Add a new row to selected environment - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Claim_package`. Use display name **Claim package**.

**Run after:** `Review_form`: Succeeded.

**Native operation:** `CreateRecordWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**cr090_intakekey** - Expression editor

```text
concat('package|',triggerBody()?['text'])
```

**cr090_invoicekey** - Expression editor

```text
if(equals(first(body('Financial_checks'))?['identity_complete'],true),concat('SYN-ENTITY|',first(body('Financial_checks'))?['vendor_id'],'|',toUpper(trim(first(body('Invoice_fields'))?['invoice_number']))),null)
```

**cr090_reviewstate** - Literal / structured value

```text
package_claimed
```

**cr090_reviewpayload** - Expression editor

```text
string(first(body('Review_form')))
```

</details>

#### Save_package

<details>
<summary>Connector / SharePoint / Create file - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Save_package`. Use display name **Save package**.

**Run after:** `Claim_package`: Succeeded.

**Native operation:** `CreateFile`. Select your approved connection; do not copy a connection ID.

**Site address** - Literal / structured value

```text
__INVOICE_SITE_URL__
```

**Folder path** - Literal / structured value

```text
/Shared Documents/ReviewPackages
```

**File name** - Expression editor

```text
concat(outputs('Claim_package')?['body/cr090_ghcpinvoicereviewid'],'.json')
```

**File content** - Expression editor

```text
string(first(body('Review_form')))
```

</details>

#### Record_package

<details>
<summary>Connector / Microsoft Dataverse / Update a row in selected environment - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Record_package`. Use display name **Record package**.

**Run after:** `Save_package`: Succeeded.

**Native operation:** `UpdateOnlyRecordWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Row ID** - Expression editor

```text
outputs('Claim_package')?['body/cr090_ghcpinvoicereviewid']
```

**cr090_reviewstate** - Literal / structured value

```text
package_ready
```

**cr090_packagefileurl** - Expression editor

```text
concat('__INVOICE_SITE_URL__',replace(uriComponent(outputs('Save_package')?['body/Path']),'%2F','/'))
```

</details>

#### Reconcile_package

<details>
<summary>Connector / Microsoft Dataverse / List rows from selected environment - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Reconcile_package`. Use display name **Reconcile package**.

**Run after:** `Record_package`: Succeeded, Failed, TimedOut, Skipped.

**Native operation:** `ListRecordsWithOrganization`. Select your approved connection; do not copy a connection ID.

**Environment** - Literal / structured value

```text
__DATAVERSE_ORGANIZATION_URL__
```

**Table name** - Literal / structured value

```text
cr090_ghcpinvoicereviews
```

**Select columns** - Literal / structured value

```text
cr090_ghcpinvoicereviewid,cr090_intakekey,cr090_invoicekey,cr090_reviewstate,cr090_packagefileurl,cr090_reviewpayload,versionnumber
```

**Filter rows** - Expression editor

```text
concat('(cr090_intakekey eq ''package|',replace(triggerBody()?['text'],'''',''''''),'''',if(equals(first(body('Financial_checks'))?['identity_complete'],true),concat(' or cr090_invoicekey eq ''',replace(concat('SYN-ENTITY|',first(body('Financial_checks'))?['vendor_id'],'|',toUpper(trim(first(body('Invoice_fields'))?['invoice_number']))),'''',''''''),''''),''),') and startswith(cr090_intakekey,''package|'')')
```

**Row count** - Literal / structured value

```text
2
```

</details>

#### Package_outcome

<details>
<summary>Function / Select - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Package_outcome`. Use display name **Package outcome**.

**Run after:** `Reconcile_package`: Succeeded, Failed, TimedOut, Skipped.

**From** - Expression editor

```text
json('[{}]')
```

**Map:** add each key exactly as shown, with the corresponding value or expression.

**status** - Expression editor

```text
if(if(equals(length(coalesce(outputs('Reconcile_package')?['body/value'],json('[]'))),1),and(equals(first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_reviewstate'],'package_ready'),not(empty(first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_packagefileurl']))),false),if(equals(actions('Record_package')?['status'],'Succeeded'),first(body('Review_form'))?['status'],'duplicate'),if(or(equals(outputs('Claim_package')?['statusCode'],401),equals(outputs('Claim_package')?['statusCode'],403)),'denied','unknown_outcome'))
```

**record_id** - Expression editor

```text
coalesce(outputs('Claim_package')?['body/cr090_ghcpinvoicereviewid'],if(equals(length(coalesce(outputs('Reconcile_package')?['body/value'],json('[]'))),1),first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_ghcpinvoicereviewid'],''),'')
```

**package_file_url** - Expression editor

```text
coalesce(if(equals(length(coalesce(outputs('Reconcile_package')?['body/value'],json('[]'))),1),first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_packagefileurl'],null),if(equals(actions('Save_package')?['status'],'Succeeded'),concat('__INVOICE_SITE_URL__',replace(uriComponent(outputs('Save_package')?['body/Path']),'%2F','/')),''),'')
```

**package_file_id** - Expression editor

```text
coalesce(outputs('Save_package')?['body/Id'],'')
```

**record_version** - Expression editor

```text
if(equals(length(coalesce(outputs('Reconcile_package')?['body/value'],json('[]'))),1),string(first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['versionnumber']),'')
```

**created** - Expression editor

```text
equals(actions('Claim_package')?['status'],'Succeeded')
```

**approval_state** - Literal / structured value

```text
not_requested
```

**requires_human_review** - Expression editor

```text
true
```

**package_json** - Expression editor

```text
if(if(equals(length(coalesce(outputs('Reconcile_package')?['body/value'],json('[]'))),1),and(equals(first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_reviewstate'],'package_ready'),not(empty(first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_packagefileurl']))),false),first(coalesce(outputs('Reconcile_package')?['body/value'],json('[]')))?['cr090_reviewpayload'],'')
```

**reason** - Expression editor

```text
concat('claim=',actions('Claim_package')?['status'],';file=',actions('Save_package')?['status'],';record=',actions('Record_package')?['status'],';reconcile=',actions('Reconcile_package')?['status'])
```

</details>

#### Set_package_result

<details>
<summary>Variable / Set variable - open exact fields</summary>

**Location:** `Source_current > True > Text_source_supported > True > Set_package_result`. Use display name **Set package result**.

**Run after:** `Package_outcome`: Succeeded.

**Variable name** - Literal / structured value

```text
package_result
```

**Value** - Expression editor

```text
first(body('Package_outcome'))
```

</details>

#### Respond_to_the_agent

<details>
<summary>Function / Respond to the agent - open exact fields</summary>

**Location:** `Respond_to_the_agent`. Use display name **Respond to the agent**.

**Run after:** `Source_current`: Succeeded, Failed, TimedOut, Skipped.

Create Text outputs in the following order. The internal keys are shown for matching expressions.

**Output status (internal text)** - Expression editor

```text
if(not(equals(triggerBody()?['text'],'__NORMAL_SOURCE_RECORD_ID__')),'denied',if(not(equals(actions('Read_approved_record')?['status'],'Succeeded')),if(or(equals(outputs('Read_approved_record')?['statusCode'],401),equals(outputs('Read_approved_record')?['statusCode'],403)),'denied','unavailable'),if(not(equals(length(coalesce(outputs('Read_approved_record')?['body/value'],json('[]'))),1)),'needs_review',if(and(not(equals(actions('Source_current')?['status'],'Succeeded')),equals(variables('package_result')?['status'],'needs_review')),'unknown_outcome',variables('package_result')?['status']))))
```

**Output record_id (internal text_1)** - Expression editor

```text
coalesce(variables('package_result')?['record_id'],'')
```

**Output result_json (internal text_2)** - Expression editor

```text
string(variables('package_result'))
```

**Output version (internal text_3)** - Expression editor

```text
coalesce(variables('package_result')?['record_version'],'')
```

</details>

<!-- END GENERATED FINANCE FIELD SHEETS -->

</details>
