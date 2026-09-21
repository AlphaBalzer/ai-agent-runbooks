# Resources and skills index

## Delivery status

The four scenario pages describe the end-to-end business process, delivery architecture,
implementation phases and test corpus. **The supplied implementation does not yet deliver that
complete process.** The executable reference coverage is selected-message assessment and response
preparation, not automated intake and action.

| Area | Recorded implementation status |
|---|---|
| Selected-message assessment | Connected reading from a fixed test mailbox, classification, reference lookup, response text and route recommendations demonstrated with synthetic data. Every output requires human review. |
| Automatic intake and downstream actions | Mail-arrival integration, forwarding, record creation, sending, document delivery and saved Outlook drafts are not implemented in this package. The workflow-to-GHCP invocation path has not been established; agent-to-workflow support is not evidence of the reverse direction. |
| Attachments and references | Up to five non-inline `.txt` attachments, each no more than 64 KB. No PDF/OCR or full-conversation retrieval. References are fictional test entries, not company policy. |
| Remaining evidence | Effective denial after immediate access revocation and independent completion of both skills remain unproven. Full acceptance remains open. |
| Packaging | Guides, skill instructions and workflow rebuild references are supplied, not an importable solution. The test agent remains unpublished. |

The [recorded results](Actual-test-record.json) distinguish observed outcomes from unproven
behavior. The existing record covers 26 Preview prompts; it does not establish full end-to-end
delivery or production approval.

Before final end-to-end handoff, complete the agreed mail-arrival and action integration and
demonstrate the complete path. The documentation's delivery checklist does not complete or
authorize those operations.

## Included assets

| Asset | Purpose |
|---|---|
| [Capability matrix](Capability-matrix.md) | Skill IDs, tools, dependencies and safety boundaries |
| [Starter cases](Synthetic-validation-cases.json) | Eight synthetic inputs and expected outcomes; observed results are recorded separately |
| [Results record](Actual-test-record.json) | Recorded outcomes, historical failures and remaining evidence gaps |
| [shared-mailbox-intake](../Skills/shared-mailbox-intake/SKILL.md) | Read and assess evidence |
| [grounded-reply-drafting](../Skills/grounded-reply-drafting/SKILL.md) | Prepare review-only text |
| [Agent instructions](Agent-instructions.md) | Copyable Markdown block containing the recorded review-only instruction revision |
| [Mailbox definition](Fixed-mailbox-read.definition.json) | Sanitized native rebuild reference |
| [Reference definition](Approved-reference-lookup.definition.json) | Three-entry test catalogue |

## Using the resources

After environment/cost approval, upload each skill through **Build > Skills >
Upload a skill**. YAML name and folder must match the matrix ID. Configure the
named tools separately; importing Markdown does not create a connection or flow.

Definitions are rebuild references, not importable solutions. Recreate and validate
in the supported designer. The repository authoring helper is not a runtime skill.

Both skills have been imported. Intake loading was observed; independent completion and
drafting attribution remain unproven. The included skills and tools do not send, forward,
create records, save drafts, move, delete, archive or mark mail.

---

## Workflow Setup

### 1. Prepare the connection

Use an approved test environment, maker permissions and capped capacity. Check DLP and region.
Select one dedicated shared mailbox and a licensed delegate. Full Access is not read-only:
restrict the exposed operations separately, grant no sending permissions for the review-only
exercise and block direct shared-mailbox sign-in.

### 2. Build the mailbox read

In **Build > Tools > Add > Workflow**, use
[Fixed-mailbox-read.definition.json](Fixed-mailbox-read.definition.json) as the field/expression
reference. Create:

`When an agent calls the flow -> Get email -> Select -> Respond to the agent`

| Node | Configuration |
|---|---|
| Agent-call trigger | One required Text input, title `messageId`, generated key `text`. No mailbox input. |
| Outlook Get email | Operation `GetEmailV2`; bind the approved end-user connection. Message ID comes from the trigger. Fix Original mailbox address to the actual test mailbox in place of `__TEST_SHARED_MAILBOX__`. Include attachments and sensitivity-label flags: true. |
| Select | Copy `definition.actions.Select.inputs.from` and its mappings for `source_id`, `name`, `status` and `text`. Keep the node name `Select`. |
| Respond | Add the nine outputs below in order. Copy expressions from `definition.actions.Respond_to_the_agent.inputs.body`. Under **More options > Settings > Run after**, select Succeeded, Failed, TimedOut and Skipped for Select. |

| Output title | Type / generated key |
|---|---|
| body | Text / text |
| source_id | Text / text_1 |
| subject | Text / text_2 |
| sender | Text / text_3 |
| has_attachments | Yes/No / boolean |
| status | Text / text_4 |
| error_code | Text / text_5 |
| attachments | Text / text_6 |
| attachment_status | Text / text_7 |

Use expression tokens, not quoted strings. Inspect `Get_email` and `Select` in Code view;
adjust mappings if generated names differ. Preserve explicit failure statuses.

After the applicable approval, save and publish **the workflow only**. Attach it as
`ReadSharedMailboxMessage`. Remove any unrestricted direct mailbox tool that bypasses the
fixed-mailbox boundary.

### 3. Build the reference lookup

Use [Approved-reference-lookup.definition.json](Approved-reference-lookup.definition.json):

1. Create an agent-call trigger with one required Text input `reference_id`, key `text`.
2. Add a Respond node with four Text outputs in order: `status`, `source_id`, `text`, `version`.
3. Copy the corresponding response expressions from the definition.
4. Save/publish the workflow after approval and attach it as `LookupApprovedReference`.
5. Reload the saved agent and confirm exactly the two intended tools, with nine mailbox
   outputs and four reference outputs.

The fixed catalogue contains `REF-POLICY-INTAKE`, `REF-STATUS-SR4421` and `REF-ROUTES`.
These are fictional training references. Unknown keys return `not_found`, not generated policy.
Production sources require their own approved connection, access controls and evaluation.

### 4. Inspect the actual result

Use the [connected walkthrough](../4.Sample-prompts.md#connected-preview-walkthrough).
A node test calls a real connector even when its inputs are mocked. A whole-workflow test can
save/publish changes or activate a trigger. Obtain approval for the actual effect before testing.

Inspect business `status`, source IDs and effects rather than relying on a green execution badge.
Keep consent continuations in the same test conversation and retain failed attempts separately.

---

## Trainer Walkthrough

| Step | Page or screen | Explain |
|---|---|---|
| Introduce the problem | [Overview](../1.Overview.md) | Shared mailbox workload, business outcomes and the GHCP investigation step. |
| Explain the parts | [Architecture](../2.Architecture.md) | Skills guide assessment; tools read sources; workflows and people control effects. |
| Show the build | [Runbook](../3.Runbook.md) | Follow the phases, then use the concrete setup above for the supplied assessment components. |
| Run one example | [Connected Preview walkthrough](../4.Sample-prompts.md#connected-preview-walkthrough) | Prepare the email, obtain the ID, paste the prompt and inspect the result. |
| Show an exception | Conflicting-reference test | Both quotes, explicit uncertainty and human review instead of a guess. |
| Close with coverage | [Delivery status](#delivery-status) | Distinguish a demonstrated assessment from the complete arrival-to-action process. |

Teach one step at a time. Explain placeholders before asking learners to replace them. Rehearse
the exact connected path before class. If a tool is unavailable, stop and label any saved run
as a recorded example rather than claiming live success.

---

## Platform References

- [GitHub Copilot harness overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/overview)
- [Upload a skill](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/skills-add-existing)
- [Add a workflow tool (preview)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/tools-add-workflow)
- [Workflow designer and test behavior](https://learn.microsoft.com/en-us/microsoft-copilot-studio/workflows-experience/flow-designer)
- [Office 365 Outlook connector](https://learn.microsoft.com/en-us/connectors/office365/)

The workflow-tool guidance confirms the agent calling a workflow. It does not establish a
mail-triggered workflow calling a GHCP agent. Verify the required intake integration independently.
