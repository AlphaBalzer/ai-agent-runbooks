# Resources and skills index

| Asset | Purpose |
|---|---|
| [Capability matrix](Capability-matrix.md) | Skill IDs, tools, dependencies and safety boundaries |
| [Starter cases](Synthetic-validation-cases.json) | Eight synthetic cases; not executed |
| [Results record](Actual-test-record.json) | Actual results stay `not_run` until observed |
| [shared-mailbox-intake](../Skills/shared-mailbox-intake/SKILL.md) | Read and assess evidence |
| [grounded-reply-drafting](../Skills/grounded-reply-drafting/SKILL.md) | Prepare review-only text |
| [Pilot instructions](Pilot-agent-instructions.txt) | Tested instruction revision |
| [Mailbox definition](Fixed-mailbox-read.definition.json) | Sanitized native rebuild reference |
| [Reference definition](Approved-reference-lookup.definition.json) | Three-entry test catalogue |

After environment/cost approval, upload each skill through **Build > Skills >
Upload a skill**. YAML name and folder must match the matrix ID. Configure the
named tools separately; importing Markdown does not create a connection or flow.

Definitions are rebuild references, not importable solutions. Recreate and validate
in the supported designer. The repository authoring helper is not a runtime skill.

Both skills imported; 26 Preview prompts. Intake loading observed; completion and
drafting attribution remain unproven. Denial and final acceptance remain open.
