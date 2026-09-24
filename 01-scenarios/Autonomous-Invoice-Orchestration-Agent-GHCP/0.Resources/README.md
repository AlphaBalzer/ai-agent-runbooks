# Resources and Delivery Status

## Supplied Resources

| Resource | Purpose |
|----------|---------|
| [Agent-instructions.txt](Agent-instructions.txt) | Copy into the Copilot Studio agent Instructions field. |
| [Complete_Test_Invoice_READY_FOR_APPROVAL.pdf](Complete_Test_Invoice_READY_FOR_APPROVAL.pdf) | Synthetic, complete invoice for approval-path testing. |
| [Incomplete_Test_Invoice_NEEDS_REVIEW.pdf](Incomplete_Test_Invoice_NEEDS_REVIEW.pdf) | Synthetic invoice for exception-path testing. |
| [invoice-review skill](../Skills/invoice-review/SKILL.md) | Upload through **Build → Skills → Add skill**. |

## Delivery Status

| Capability | Evidence as of 24 September 2026 |
|------------|----------------------------------|
| Published Invoice Orchestration Agent | ✅ Present |
| GPT-5 Chat model | ✅ Present |
| Read-only SharePoint tool | ✅ Present |
| `invoice-review` skill | ✅ Present, but the repository version is corrected to match direct SharePoint PDF review |
| Knowledge sources | ➖ None configured or required |
| Published intake and approval workflow | ✅ Present |
| PDF saved to SharePoint | ✅ Verified |
| Agent response parsed | ✅ Verified |
| Review package saved to SharePoint | ✅ Verified |
| Auto Invoice Reviews record created | ✅ Verified |
| `NEEDS_REVIEW` notification | ✅ User-reported successful |
| Live approval request | ✅ Verified |
| Approved outcome notification | ✅ Verified |
| Rejected outcome notification | 🧪 Configured; rejection test evidence not yet captured |

## Deployment Note

Use the agent instructions, skill and test documents in this folder as one coherent build.
The skill reads the exact source PDF directly through the agent's SharePoint tool, while the
workflow owns all writes and approval actions. Do not mix these files with earlier draft
architectures or flow definitions.
