---
name: pragmatic-programmer
description: Diagnose root causes or improve maintainability, coupling and architecture. Use for substantial debugging or refactoring, not routine feature edits.
---

# Pragmatic Programmer

Make the requested behavior reliable and future changes easier. This skill owns diagnosis and intervention choices for substantial debugging and changeability work; ordinary implementation follows the applicable global and project guidance.

## Diagnose The Problem

Establish intended behavior from the request and accepted decisions, then examine what actually happens. Investigate a vague failure before naming its cause.

Trace a failure to the earliest incorrect state using the error, relevant execution path and evidence. Test plausible explanations where it changes the diagnosis; do not suppress symptoms, widen retries or add catch-all guards without a reason established by the failure. Several interacting causes may need resolving.

For changeability, identify the next likely change and what makes it expensive or risky. Useful clues include duplicated business knowledge, hidden coupling, unclear rule/state ownership, interfaces that spread a local change, and behavior that works by coincidence. Distinguish verified contracts and platform constraints from habits or assumed limitations.

## Choose The Intervention

| Situation | Useful approach |
| --- | --- |
| The defect and requested change are local | Local repair |
| The same knowledge has multiple owners | Extract or consolidate its authority |
| Changes cross unnecessary boundaries | Repair the interface or ownership |
| A redesign has uncertain integration across layers | A small end-to-end implementation slice to test the architecture |
| Future requirements are unclear | Keep the current solution easy to replace |

Preserve required behavior and contracts, and verify unfamiliar patterns before relying on them.

DRY concerns knowledge, not similar text: similar-looking blocks may represent different concepts, while differently written blocks may encode the same business rule. Search existing owners before adding another abstraction. Keep the rule and its callers consistent without combining unrelated concepts.

Use [mece-thinking](../mece-thinking/SKILL.md) when the actual problem is overlapping/mixed-level concepts, broken state/lifecycle partitions or a taxonomy that must be repaired. Ordinary local ownership cleanup does not need a taxonomy exercise.

Explain the supported cause or changeability problem, the proposed intervention and relevant verification in the format the task needs. For additional principles, consult the book itself, *The Pragmatic Programmer* by Andrew Hunt and David Thomas, selectively; its tips are context, not commands to run every workflow.
