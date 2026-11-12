---
name: mece-thinking
description: >-
  Use when asked to make a framework MECE, try to break a model, build one exhaustive level of buckets, or when the user says 'think MECE'. Covers issue trees, decision trees, taxonomies and segmentations.
---

# MECE Thinking Partner

Be a rigorous thinking partner: preserve the model’s **utility** while making it truly MECE.

## Core definition

MECE = a **partition** of a clearly defined **parent set** at one **abstraction level**, with a clear **assignment rule**:

- **Mutually exclusive**: any item maps to exactly one bucket.
- **Collectively exhaustive**: every item maps to some bucket.

If the model is conceptual, still make the parent set + level explicit so overlap/missing can be tested.

## Acceptance rule: “Can I break it?”

A model is MECE only when you **cannot** find:

- any overlap (one item fits 2 buckets), and
- any same‑level missing bucket.

Probe realistic overlap and missing cases for the stated parent set. Repair demonstrated failures. Stop when those checks pass, and state any boundary that cannot be established from available evidence.

## Non‑negotiables

- Make the **parent set + level** explicit (or state assumptions).
- Do **not** mix bases/levels inside one MECE list.
- Do not use an arbitrary or hidden tie-break to make overlapping definitions appear exclusive. Explicit predicates can define a partition; a preferred label alone cannot.
- **Preserve utility**; do not oversimplify into a different model unless overlap forces it.
- **Reconcile existing terms first**; do not invent new buckets until you’ve tried to make the given terms MECE.
- If a doc says a section is “not MECE”, treat it as out of scope (or as a precondition), not a failure.

## Narrow utility exception: `~MECE`

Strict MECE is the default. Use `~MECE` only for small, identified departures when a concrete comparison supports **10–20x or greater utility** than the strongest practical perfectly MECE alternative.

- Show the strict alternative first, then identify each overlap or gap in the proposed `~MECE` version and the cases it affects.
- Explain the source of the large utility gain: for example, a demonstrated reduction in decision effort while preserving required distinctions. Compare the same task and success criteria. Do not compare against an artificially weak strict alternative.
- Use measured evidence or a transparent, grounded estimate. If the comparison cannot support the gain, keep the strict model.
- Keep each departure bounded and visible. State how affected cases will be handled without hiding lost outcomes or duplicate counts.
- Report the choice and its basis. Never label a `~MECE` model strictly MECE.

## Structure handling

### Decision trees

- MECE applies **within each decision node** (sibling branches), not across the whole sequence.
- If there is a utility‑first step (e.g., “do we have data?”), allow it as an explicit **pre‑check**, then apply MECE to the diagnostic nodes.
- If the tree mixes actions with diagnoses, split: keep actions as playbooks, diagnoses as MECE buckets.

### Equation‑based models

- First check the equation's definitions, units, domain, and assumptions. A partition cannot make an invalid equation valid. Correct a demonstrated error or state an unverified assumption before using the equation as an anchor.
- **Reconcile** categories to the equation terms first (add missing terms like Risk if the formula includes them).
- Only after reconciliation, split **drivers** vs **constraints/enablers** into separate MECE models if needed.
- If the equation level is ambiguous (Profit vs FCF vs EV vs Growth), pick one, state it, and proceed.

## Apply and report

Establish the purpose and parent set, unit, level, and structure. Reconcile existing terms, probe realistic overlaps and gaps, and repair the affected partition. Stop when the requested model passes.

Report in this shape unless the user asks otherwise (see [example-response.md](references/example-response.md)):

1. **Verdict**: MECE / `~MECE` under the utility exception / Not MECE, with 1–2 reasons
2. **Parent set + level**: state assumptions
3. **Break attempts**: overlap and missing-bucket probes, and what changed
4. **MECE version** when fixes are requested: buckets, definitions, assignment rules
5. **Notes on utility**: what was preserved, what changed, why; for `~MECE`, the strict alternative, concrete comparison and bounded departures

## Language

Match the user’s language.

Past failures used for testing: [eval-cases.md](references/eval-cases.md).
