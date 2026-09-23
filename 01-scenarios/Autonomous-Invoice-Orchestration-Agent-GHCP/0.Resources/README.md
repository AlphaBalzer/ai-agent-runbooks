# Resources - Autonomous Invoice Orchestration Agent (GHCP)

**Same PDF invoice process. One small GHCP review step.**

## What to use

| Resource | Purpose |
|---|---|
| [Main runbook](../3.Runbook.md) | Build sequence, expected results and original screenshot links. |
| [Agent instructions](Agent-instructions.txt) | Copy into the new GHCP agent's Instructions field. |
| [invoice-review skill](../Skills/invoice-review/SKILL.md) | The single Markdown file to upload under Build > Skills. |
| [Component guide](Capability-matrix.md) | Which parts stay the same and what the skill needs. |
| [Original sample PDF](../../Autonomous-Invoice-Orchestration-Agent/0.Resources/Sample_Invoice.pdf) | First digital-PDF example for the approved exercise. |
| [Original runbook](../../Autonomous-Invoice-Orchestration-Agent/3.Runbook.md) | Intake, storage, document extraction, HTML form and manager-approval examples. |

The instruction and skill files are authored for the **simplified build target**, not yet
imported or validated against its PDF workflows. They do not provision tools or connections.
Do not replace the existing test agent's instructions with them until the matching flow
contracts are configured.

The skill reviews extraction and accounting-reference results. It needs **no additional
connector or lookup service**. Keep the original reference lookup in the parsing workflow.

## Delivery status

| Item | Status as of 23 September 2026 |
|---|---|
| Simplified PDF-to-approval path | Guide, instructions and one skill supplied. Runtime integration and end-to-end demonstration outstanding. |
| Earlier isolated text pilot | Published agent read an invoice, checked fictional references and created an HTML form that rendered in SharePoint. |
| Sequential duplicate replay | Returned the existing HTML package without a second file or package row. |
| Known remaining issue | Replay shortened attachment citation IDs. Stored package identity was correct; exact-citation acceptance is incomplete. |
| PDF extraction, automatic intake, manager approval and notifications | Not demonstrated for this GHCP scenario. Approval remains disabled in the earlier pilot. |

Keep the distinction: a working text-pilot form is not a finished PDF-to-approval solution.
No payment execution or ERP posting is included.

## Earlier test material

The [Archive](Archive/README.txt) contains the old reconstruction JSON, fixtures, raw results
and snapshot-specific instructions/skills. These are **optional historical references**, not
files a learner must import or understand to build the simplified scenario.

The complete [earlier illustrated guide and field sheets](https://github.com/AlphaBalzer/ai-agent-runbooks/tree/77a9c27c9e85508d80bf3e6f618b08b8953f35a1/01-scenarios/Autonomous-Invoice-Orchestration-Agent-GHCP)
remain available at their fixed revision. Archive files are unchanged and have not been
relabelled as current PDF evidence.

## Screenshots

Use the original runbook's linked screenshots to explain its supporting flows. They are
reference illustrations, not screenshots of the proposed simplified GHCP deployment.

[Upload a skill](Images/02-upload-skill.png) shows the actual GHCP upload dialog. The other
images in [Images](Images/) record the earlier two-skill text pilot and its September 21
component result; do not use them to claim the one-skill PDF path is built.

Browser/account chrome was excluded from those captures and environment/site values masked.
No successful approval or PDF result is illustrated because neither has been demonstrated.
