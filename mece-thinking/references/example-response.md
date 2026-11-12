# Example: Repair an overlapping task model

User model: “All tasks are urgent, important, or optional.”

## Verdict

Not MECE. A task can be both urgent and important. A required task can also be neither urgent nor important under the current definitions.

## Parent set and level

Parent set: the tasks in the agreed work queue, assessed at the same time.

Unit: one task. Define urgency as whether the task has an actionable deadline before the next planning review. Define importance as whether it materially supports an agreed outcome or binding requirement. These definitions are assumptions until checked against the user's queue.

## Strict repair

Use two independent yes/no axes. Their cross-product gives four exclusive buckets:

1. Urgent and important.
2. Urgent and not important.
3. Not urgent and important.
4. Neither urgent nor important.

Every task has one urgency value and one importance value. If a value is unknown, record the missing fact before assigning that task; do not guess or silently omit it. “Optional” is a separate authorization or obligation attribute. It does not replace either axis.

## Break attempts

- A required report due tomorrow fits bucket 1 if it supports a binding requirement.
- A low-value request due tomorrow fits bucket 2.
- Important work with no deadline before the next review fits bucket 3.
- A discretionary task with no relevant deadline or material outcome fits bucket 4.

The predicates are exclusive and exhaustive once their values are known. The usefulness of the chosen urgency and importance definitions still needs a task-specific check.

## Utility

The repair preserves both urgency and importance instead of choosing a “primary” label. It does not itself decide what to do first; capacity, dependencies, and authority still matter.

There is no evidence here for a 10–20x utility gain from accepting overlap. Use the strict version. If another case supports the skill's narrow `~MECE` exception, show that comparison and disclose its specific departures.

## Equation caution

For an equation-based model, validate the equation before partitioning its terms. For example, `value = cash flow / risk` is not a usable general valuation equation when “risk” means an undefined probability or volatility. Defining buckets around those words would not repair the missing model assumptions.
