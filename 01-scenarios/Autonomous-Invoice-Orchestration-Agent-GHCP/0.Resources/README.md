# Resources and skills index

| Asset | Purpose |
|---|---|
| [Capability matrix](Capability-matrix.md) | Two skill IDs and separate workflow operations |
| [Starter cases](synthetic-invoice-fixtures.json) | Ten synthetic cases plus variants; not executed |
| [Results record](validation-record-template.json) | Actual results stay `not_run` until observed |
| [invoice-evidence-extraction](../Skills/invoice-evidence-extraction/SKILL.md) | Read-only source-linked extraction |
| [payment-request-review](../Skills/payment-request-review/SKILL.md) | Controlled review-package preparation |
| [Pilot instructions](Pilot-agent-instructions.txt) | Saved bounded read/reference/package instructions |
| [Intake rebuild](Invoice-intake.definition.json) | Operator-only source persistence |
| [Record read rebuild](Invoice-record-read.definition.json) | Fixed-scope saved snapshot read |
| [Reference rebuild](Finance-reference.definition.json) | Approved fictional catalogue |
| [Package rebuild](Generate-review-package.definition.json) | Bounded normal review-file component |

After environment/cost approval, upload each file through **Build > Skills >
Upload a skill**, then configure the separately named tools. YAML name, folder
and matrix ID match. Import is not deployment or proof of permissions.

The `.github/skills/` authoring helper is not an Invoice runtime skill.

Skills imported September 18; components demonstrated September 21.
Agent availability is inconsistent; approval untested. No deployable package supplied.
