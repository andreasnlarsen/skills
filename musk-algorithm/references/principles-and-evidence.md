# Principles, reasons, and evidence

Research checked: 2026-10-31. This reference explains how the skill was derived. It is a reasoned interpretation of an engineering method, not an empirical demonstration of universal effectiveness.

## Evidence and attribution

Use three distinct categories:

- **Stated:** Musk supplies the explanation in a retrieved primary interview, or the supplied book attributes it to him. Label book-only details accordingly.
- **Disclosed:** A company describes its own operations. This confirms a reported practice, not independent proof that the practice caused its success.
- **Inference:** An extension developed for this skill. Evaluate it against the present system instead of attributing it to Musk.

### Source record

**B — Supplied book.** Eric Jorgenson, *The Book of Elon* (2026), especially “The Algorithm,” “Simplicity Wins,” “Attack the Constraint,” and “Speed Is Both Offense and Defense.” In the edition consulted, “The Algorithm” occupies PDF pages 113–118; its sources are notes 324–329. The book explicitly says it edits, combines, and recontextualizes interviews. Treat it as an edited anthology, with OCR as a further source of possible error. It is not a verbatim primary transcript. The skill remains usable without a copy of the book.

**L — Direct interview.** [Lex Fridman #438, official transcript](https://lexfridman.com/elon-musk-and-neuralink-team-transcript/), 2024-08-02, Musk’s segment around 00:44:08–00:48:36. The retrieved passage directly confirms the five-step order, the danger of answering a wrongly framed question, overcautious retention, and wasted work from automating before deleting. His recollection of painful omissions explains the restoration heuristic. This is first-person reasoning, not a controlled test. The preceding discussion, around 00:42:42, also recognizes that the simplest adequate engineering solution may remain complex. Other participants speak later in the episode; do not attribute their remarks to Musk.

**S — Current corporate formulation.** [SpaceX EU prospectus, 2026-06-05, section 4.3.4.6](https://content.spacex.com/cms-assets/FINAL_Documents%20and%20Updates/SpaceX%20-%20EU%20Prospectus%20%28Approved%20by%20Bafin%29%20-%20June%205%2C%202026.pdf#page=78), PDF page 78, printed page 65. It identifies the algorithm as iterative and describes automation as following proven processes after the earlier stages. Adjacent principles connect production improvements with lower unit costs and higher throughput. This supports the conditional place of automation; it does not independently validate the entire method.

**T — Historical operational disclosure.** [Tesla Q3 2018 Form 10-Q](https://ir.tesla.com/_flysystem/s3/sec/000156459018026353/tsla-10q_20180930-gen_0.pdf#page=52), PDF page 52, printed page 52, describes problems ramping fully automated Model 3 operations and reductions to semi-automated or manual processes. It also acknowledges resulting labor costs and possible further bottlenecks. This corroborates a real tradeoff between automation, production readiness, and labor. It does not establish that every robot removed was unnecessary, or that manual work is always preferable.

**Originals located, not fully retrieved here.** Everyday Astronaut’s [Starbase tour part 1](https://www.youtube.com/watch?v=t705r8ICkRw) (2021-08-03) and [part 2](https://www.youtube.com/watch?v=SA8ZBJWo73E) (2021-08-07) are the originals cited in B for several details. Their publication metadata was located, but their complete primary transcripts were not retrieved during this run. The publisher’s article repeatedly timed out. Use B for those detailed attributions; do not claim that a separate direct viewing corroborated them. No aggregator transcript was treated as authoritative.

## What the sequence is doing

The five decisions address different possible errors. A wrong requirement misdirects effort; an unnecessary component creates avoidable effort; a cumbersome necessary implementation wastes effort; a slow adequate method delays value; and a labor-intensive proven method can limit repetition or scale. The sequence prevents a later improvement from disguising an earlier mistake. This is a synthesis of B, with the order independently corroborated by L and S.

The reasons below are deliberately non-exhaustive. A reason may be decisive in one application and irrelevant in another. The motivation for adopting the sequence also differs from the economic justification for a particular change within it.

## 1. Question requirements: correct the premise

**Reasons attributed in B:**

- A solution can be technically excellent while meeting a badly chosen requirement. Requirements therefore need examination before execution quality becomes the main concern.
- Intelligence, status, or expertise can make a request less likely to be challenged. The point of scrutiny is fallibility, not hostility toward expertise.
- A department label can conceal an old assumption, misunderstanding, or requirement nobody currently endorses. A named person makes the justification available for discussion and revision.

**Further interpretation:** Requirements define which solutions can even be considered. A more restrictive specification can eliminate good options before any design comparison occurs. Separating ends from means can expose alternatives that faster execution would never reveal.

**What to carry forward:** Ask what observable result the constraint protects and what would go wrong without it. Distinguish a verified physical limit from an assumption about how to meet that limit. Finding the author explains provenance; finding the current owner enables an accountable decision. Neither person’s title settles whether the requirement is sound.

**Limit:** A statement that everyone can be wrong does not make every requirement wrong. A user preference, a contractual commitment, and a physical constraint require different treatment. The method permits examination; it does not grant authority to waive them.

## 2. Delete: remove the source of unnecessary burden

**Reasons attributed in B:**

- Removing an unnecessary component can also remove equipment and process steps built to support it. In the battery-mat account, Musk describes teams giving conflicting explanations, testing the alleged function, and eliminating the associated operation. The generalizable point is testing necessity, not copying that deletion.
- Added rocket mass can require further support elsewhere. The lesson is dependence: a local addition can impose costs outside its immediate location. The book’s illustrative recursion factor is specific to that account, not a universal multiplier.
- Remembering a costly omission can encourage excessive retention. Permitting some restoration helps challenge that conservative bias instead of interpreting every restoration as failure.

**Further interpretation:** Deletion can avoid future coordination, inspection, failure handling, and changes. It can also create learning: a controlled omission is a test of the belief that a component is necessary. These savings must be established in the actual system; hidden downstream work can reverse them.

**What to carry forward:** Preserve the useful function rather than the artifact by habit. Compare no component, a smaller substitute, and the existing component. Choose a test that can detect the loss that matters, including delayed or infrequent failures where relevant. A missing complaint or an unused dashboard is not sufficient evidence of no dependency.

**Limit:** No source reviewed here supplies a statistical calibration for the 10% figure. Musk states it strongly; this skill carries forward its purpose of countering overcautious retention rather than imposing the number as a universal target. Zero restorations neither proves success nor proves insufficient deletion; assess how strongly necessity was tested and whether retained work is justified. A reversible trial and an irreversible deletion have different expected costs.

## 3. Simplify or optimize: improve necessary work as a system

**Reasons attributed in B:**

- Fewer unnecessary elements can reduce purchases, operations, and potential failure points.
- A sequence of locally sensible component decisions can create a difficult combined system. B’s example of different materials illustrates how joining methods and other interfaces can become burdensome.
- The habit of solving the given question can keep skilled people occupied with refinement before questioning whether the thing belongs at all.

**Further interpretation:** A simpler adequate system can require less explanation, coordination, diagnosis, and revision. Better visibility can make future learning cheaper. Optimization is broader than reducing a count: retaining more of one resource can be worthwhile if it materially improves the system’s objective.

**What to carry forward:** Examine total cost and achieved behavior. Combining components may reduce interfaces while increasing replacement cost or making failures harder to isolate. A shorter function can conceal greater coupling; a longer but clear implementation may be easier to change. Redundancy can serve a necessary reliability function.

**Limit:** Do not translate the method into minimum lines of code, minimum parts, or minimum checks regardless of outcome. Do not copy the anthology’s mathematical wording about accumulated manufacturing variance as a general formula; the relevant qualitative issue here is interaction among parts, not a claim that variances universally multiply.

## 4. Accelerate: improve the time dimension that matters

**Reasons attributed in B:**

- More useful output from the same productive assets can avoid the cost of equivalent additional capacity.
- Delay can consume resources before value arrives and postpone useful results.
- An ability to improve products faster can matter competitively. B discusses innovation rate as a reason for speed; this is wider than the narrow wording of algorithm step four.

**Further interpretation:** Shortening the time between an idea and discriminating feedback can allow more informed corrections within the same period. This is a learning benefit, conditional on feedback being relevant and reliable. It is not evidence that a rushed launch always teaches more or costs less.

**What to carry forward:** Identify the limiting stage and the metric. A task’s processing time is different from end-to-end elapsed time; throughput is different from labor used per unit. Remove waits or improve a constraint when that changes the system’s result. Faster activity away from the constraint can merely create a queue. If approval takes two days and drafting takes two minutes, a faster draft may not shorten delivery materially.

**Limit:** The preceding stages need adequate investigation, not infallible completion. A small experiment may accelerate learning about a requirement. Speed must be judged alongside useful output and consequences; physical time, error detection, and dependencies may constrain it.

## 5. Automate: make useful repetition economically sound

**Reasons attributed in B:**

- Automating before removing unnecessary work can spend capital and engineering effort on operations later eliminated.
- Speeding and refining the wrong automated operation can add more sunk effort before the underlying mistake is found.

**Further interpretation:** Delaying a large commitment to automation can preserve cheaper redesign options. Automation can reduce recurring effort and improve consistency or capacity. Its value depends on the cost of building and running it, the useful repetitions it will perform, and how often the process changes. These are engineering and economic explanations used by this skill; do not invent a quotation in which Musk presents them as a complete list of his personal motives. S supports throughput and unit-cost objectives; T demonstrates that a practical manufacturing system can mix levels of automation.

**What to carry forward:** Compare the whole workflow before and after. Include setup, exceptions, supervision, repairs, integration, and replacement. Manual investigation can reveal variation that should shape the eventual tool. Where a machine is needed to measure a phenomenon or execute the experiment at all, such an enabling tool can precede a settled production process. The sequencing concern is premature commitment of the workflow, not a ban on using tools to learn.

**Limit:** Neither AI nor deterministic code proves that the task was necessary. Conversely, variable inputs do not automatically rule automation out: the question is whether its acceptable operating conditions and failure handling are understood. A low-frequency task can still warrant automation for a sufficiently valuable reason. High volume alone does not make a badly framed process worth scaling.

## Transfer and evidence discipline

This skill treats factory stories as evidence about a reasoning pattern. It does not export factory-specific risk tolerance, numerical targets, staffing preferences, or physical designs into other domains. It also does not infer that every organization needs a full five-stage transformation.

For a new application, connect the action to an explicit causal hypothesis and a possible disconfirming observation. Distinguish an observed improvement from the explanation for it. For example, removing a report may save preparation time while harming a later decision; measuring only the time saved would not establish the intended outcome.

The primary sources establish that Musk and SpaceX describe the sequence this way, and that premature automation has had reported operational costs. The source set does not establish an optimal deletion rate, a universal five-stage law, or independently measured effectiveness across every business and personal context. Use the principles as hypotheses to reason and test with, not as proof by celebrity.
