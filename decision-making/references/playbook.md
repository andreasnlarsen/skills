# Decision-Making Playbook

Read this file before eligible substantial company decisions, template work, strategically important company choices, or eligible requests that ask for MECE/categorical decision-model fidelity.

## Table Of Contents

- Source Of Truth
- Non-Invention Boundary
- Transcript Coverage Checklist
- Eligibility Gate
- Skill Operating Modes
- Operating Settings
- Mode Workflows
- Artifact Workflows
- Autonomous QA And Delegation
- Revision Loops
- Model Inventory
- Branch Workflows
- Detailed Tony Path Process
- Sheet-Filling Notes
- Common Mistakes To Prevent
- Skill-Meta Guard

## Source Of Truth

The user-supplied spoken model controls this skill. The durable model scope is:

**All decisions that can be made by any person in a company.**

Do not narrow a model parent set to the current user or an agent unless the sentence is only about how this skill is invoked. The decision model itself is company-universal.

The Tony Robbins TOYL decision-making source provides a six-step worksheet:

1. Outcomes in order of importance.
2. Options, with at least three options as the useful threshold for choice.
3. Consequences.
4. Evaluation.
5. Mitigation.
6. Resolve.

A spreadsheet version of this worksheet, such as a user-supplied Google Sheets template, mirrors this with outcomes, options, upside/downside scoring, comparison, mitigation, and commitment. Its formulas use `Score = Imp * Prob`; upside totals are subtracted by downside totals to get net score. The canonical probability scale is always decimal `0..1` (for example, `0.8`, not `8`). If an existing template or record uses `0..10` probability, treat it as a legacy mismatch and normalize by dividing probability by `10` before scoring.

## Non-Invention Boundary

The Tony worksheet is **not** the whole company-decision model. It is mainly the method for a path-to-outcome decision after an outcome group has been defined.

Do not invent full operating rules for branches this playbook does not specify yet. Known incomplete areas:

- Full priority-scoring method for comparing one possible company problem/outcome against all other possible company goals.
- Full process for outcome-group definition beyond the rules in this playbook.
- Full execution-governance system beyond continue/adjust/pause/cancel/reopen routing after new information.

If work falls into an underspecified branch, state the missing rule and ask or proceed with an explicit assumption.

## Transcript Coverage Checklist

Preserve these source points:

- Start by figuring out which outcome/problem/outcome group the decision is really about.
- Any company decision falls into the four-way decision-object model below.
- The outcome group uses AND relationships by default.
- Outcome-group items can be terminal outcomes, additional outcomes, ways to reach other outcomes, concerns, downsides to avoid, stakeholder/process requirements, standards, or constraints.
- Use MECE to define terms, parent sets, outcome groups, and option spaces when the structure is unclear.
- Generate at least three options when possible.
- Options can be brainstormed or derived from a full logical MECE option tree.
- MECE option trees start abstract, then sub-MECE down until concrete viable choices remain after requirements eliminate nonviable branches.
- Upsides and downsides exist relative to the outcome group.
- Score impact/importance on `0..10` and probability as a decimal on `0..1`, then compute expected effect and option totals.
- Consequence lists can be MECE, but most often important-consequence brainstorming is enough.
- After scoring, a new fourth option may appear; if so, run it through the same process.
- After choosing the best option so far, brainstorm mitigations for its downsides.
- Use MECE mitigation only when needed; mitigation is usually creative brainstorming.
- Run Munger-style inversion after outcome definition and again after options if needed.
- Inversion includes procedural failures, context-specific biases, and tactic/strategy failures.
- Person/owner selection can fail because of bias, poor cross-silo leadership skill, missing silo knowledge, or a standard mismatch.
- Hiring/assignment decisions must consider technical vs interpersonal/trait skill gaps and which deficiency is limiting or hardest to fix.
- Any option with an unlivable downside or worst case is off the table regardless of probability.
- Execution decisions can continue, adjust, pause, cancel, or reopen path/outcome/priority decisions when new information such as resources or results changes the basis.
- This skill must not be used for low-stakes, trivial, easily reversible, preference-style, casual, quick personal, or ordinary minor decisions.

## Eligibility Gate

The company-decision ontology covers all decisions that can be made by any person in a company. That does **not** mean every company decision should invoke this skill.

Use this skill only when the current request is substantial enough to justify a formal decision record.

Eligible requests include:

1. Company priority decisions: which problem, opportunity, main outcome, or outcome group deserves focus relative to other company goals.
2. Outcome-group definition decisions where success criteria need to be made explicit.
3. Path-to-outcome decisions where meaningful options, tradeoffs, consequences, and mitigation matter.
4. Execution/reopen decisions where new information may justify continue, adjust, pause, cancel, or reopen.
5. Strategic, cross-functional, resource, hiring, owner-assignment, or high-consequence operating decisions.
6. TOYL/Tony Robbins-style decision framework creation, filling, or audit.
7. Autonomous decision runs, facilitated decision records, audits, or stress-tests for substantial company decisions.

Ineligible requests include:

1. Low-stakes decisions.
2. Trivial decisions.
3. Easily reversible decisions where a formal record would be overhead.
4. Preference-style or taste decisions.
5. Casual or quick personal choices.
6. Ordinary minor decisions that do not warrant a formal decision record.

If a request is ineligible, do not run a compressed version of this framework. Answer normally or use another relevant skill.

## Skill Operating Modes

This section is about how the agent uses the skill. It is not part of the company-decision ontology.

Shape: routing tree for the current requested job, with facilitation as a separate setting.

Parent set: the primary high-utility jobs this skill supports for moving an eligible substantial company decision forward in the current request.

Buckets:

1. **Facilitated Decision Record**: the user and agent make the decision together. The agent guides the process, asks for missing judgment, fills the decision record as the work progresses, and checkpoints important choices before treating them as settled.
2. **Autonomous Decision Run**: the agent completes the decision process itself. The agent defines assumptions, researches when needed, generates outcomes and options, scores, mitigates, and recommends without waiting for user input at every step.
3. **Audit / Stress-Test Decision Record**: the user already has a decision record, sheet, plan, recommendation, or reasoning. The agent inspects it for flaws and either reports fixes or applies them if asked.
4. **Execution Reopen Triage**: a path has already been selected and execution is underway. New information or friction has appeared, and the job is to decide continue, adjust, pause, cancel, or reopen a prior decision branch.

Routing rule: first identify the requested deliverable: a new decision record, an audit of an existing record, or a response to changed execution conditions. Split a compound request into these work phases. For a new record, select facilitated or autonomous from the user's instruction about who supplies missing judgment. Audit and execution triage can also be facilitated or autonomous; do not force the same request into competing flat buckets.

Break test:

- "Fill this out in Google Sheets with me" is **Facilitated Decision Record + artifact: Google Sheets**, not a separate mode.
- "Make the whole decision analysis yourself and give me the answer" is **Autonomous Decision Run**, regardless of whether the output is chat, Markdown, Google Sheets, or Excel.
- "Review this sheet/plan" is **Audit / Stress-Test**, even if the agent later writes corrected values into the sheet.
- "We picked X, but resources/results changed" is **Execution Reopen Triage**, even if it leads back into a new path-to-outcome decision.

These mode names preserve the supported jobs. Deliverable routing and facilitation are separate choices, as described above. Artifact, rigor, and delegation are also settings that can apply to more than one job.

## Operating Settings

Choose these after the mode. Do not use them as modes.

### Artifact

Parent set: supported artifact surfaces in this skill.

Options:

1. Chat: inline decision record for eligible decisions when no external artifact is requested; less durable than Markdown, Google Sheets, or Excel.
2. Markdown: durable text record, good for review, versioning, and handoff.
3. Google Sheets: preferred visual/durable worksheet when the user wants a real TOYL-style decision record filled out collaboratively or by the agent.
4. Excel/XLSX: local file or export fallback, useful when Google Sheets is unavailable, when the user needs a file artifact, or when spreadsheet tooling is easier locally before import.

Use rule: a decision record is not optional in facilitated or autonomous full runs. If no spreadsheet or Markdown artifact is requested, the chat answer still needs to contain the record structure.

### Rigor

Parent set: supported rigor levels for applying this skill.

Options:

1. Standard: full mode workflow with outcome group, inversion, options when path-like, scoring when needed, mitigation, and commitment.
2. Adversarial: standard workflow plus deliberate break attempts against parent sets, outcomes, option completeness, unlivable downsides, assumptions, scoring sensitivity, owner fit, and revision triggers.

Use rule: use adversarial when the decision is important, strategically consequential, likely to hide a missing option/outcome, or when the user explicitly asks for an ultra-thorough review.

### Delegation

Parent set: supported delegation levels for checking beyond the primary run.

Options:

1. None: one agent performs the work and self-checks.
2. Reviewer pass: a separate review pass, by the same agent or an available reviewer, checks for flaws after a draft.
3. Subagent checkpoints: independent agents check specific gates such as outcome group, option space, inversion, scoring, mitigation, and artifact integrity.

Use rule: subagent checkpoints are desirable for big autonomous runs, but use them only when the user asks for or authorizes them and the current environment/tool policy allows them. If independent checkpoints are not used, explicitly perform the same checkpoint list as self-review and state that no independent pass was run.

### Revision Loop

Parent set: places where a decision run may need to loop backward.

Targets:

1. Decision object: the request was classified at the wrong branch.
2. Outcome group: a consequence, inversion finding, stakeholder requirement, or constraint reveals a missing or wrong outcome.
3. Options: the option set is not complete, not concrete, or includes an unlivable downside.
4. Scoring: scores are inconsistent, sensitive, or based on unclear assumptions.
5. Mitigation: mitigations change the option enough to require re-scoring.
6. Execution triage: new information changes the decision basis after commitment.

Use rule: loops are not failure. They are part of the process. When a loop changes a previous section, update downstream reasoning and the artifact instead of leaving stale conclusions in place.

## Mode Workflows

### Facilitated Decision Record

Use when the user is the decision-maker and wants help working through an eligible substantial company decision.

Workflow:

1. Select artifact and rigor. If the user wants a visual framework, default to Google Sheets unless they asked for Excel or Markdown.
2. Establish decision object using the four-way company decision taxonomy.
3. Ask only for missing judgment that materially changes the next step.
4. Fill or update the record as the decision develops; guidance and record-filling are one workflow, not separate modes.
5. Checkpoint major judgments: outcome group, option set, unlivable downside filter, scoring assumptions, mitigation choices, and final commitment.
6. Keep unresolved items visible as assumptions or open questions instead of silently deciding them.

Done criteria:

- The decision record is filled enough to show the decision object, outcome group, inversion, options when relevant, scoring when relevant, mitigations, commitment, and open assumptions.
- The user has supplied or approved the judgment calls that should not be invented by the agent.

### Autonomous Decision Run

Use when the user wants the agent to do the whole analysis for an eligible substantial company decision.

Workflow:

1. State the mode and whether artifact, rigor, and delegation were specified or inferred.
2. Define the decision object and outcome group from available context.
3. Mark inferred outcomes, assumptions, and missing information explicitly.
4. Generate options and run the Tony path process when the decision is path-to-outcome.
5. Research current/external facts when they materially affect the decision and the environment allows retrieval.
6. Run inversion and unacceptable-downside filtering before treating expected-value scoring as decisive.
7. Recommend an option, mitigations, first action, owner if inferable, review trigger, confidence, and what would change the recommendation.
8. For big or high-stakes decisions, use reviewer/subagent checkpoints if available and authorized; otherwise run explicit self-checks at the same gates.

Done criteria:

- A decision-maker could read the output and understand the recommendation, assumptions, confidence, missing information, reversal triggers, rejected options, and required mitigations.
- The output does not hide agent-supplied judgment as if it came from the user.

### Audit / Stress-Test Decision Record

Use when an eligible substantial company decision already exists in a sheet, document, plan, message, or reasoning.

Workflow:

1. Identify the artifact and current decision object.
2. Check whether the parent set is wrong, narrowed, or mixed with skill-operation categories.
3. Check outcome group completeness, AND relationships, definitions, and stakeholder/constraint/standard items.
4. Check option completeness, abstraction level, requirement eliminations, and unlivable downside filtering.
5. Check upsides/downsides relative to the outcome group, scoring consistency, probability/impact assumptions, and sensitivity.
6. Check inversion coverage: procedural, bias, tactic/strategy, owner fit, skill deficiency, and execution reopen risks.
7. Report findings first, then provide the corrected record or exact patch/write plan when requested.

Done criteria:

- The user can see the highest-risk flaws and the concrete correction for each.
- If edits are requested, the artifact is updated without overwriting formulas or unrelated content.

### Execution Reopen Triage

Use when an eligible substantial company decision is already in execution.

Workflow:

1. Identify the original selected path, outcome group, and commitment if known.
2. Identify new information and classify it with the Execution New-Information Model.
3. Decide the lowest branch whose basis is invalidated: execution only, path-to-outcome, outcome group, or company priority.
4. Recommend continue, adjust, pause, cancel, or reopen.
5. If reopened, route to the relevant branch workflow and preserve useful prior work.

Done criteria:

- The answer names the action to take now and why the new information does or does not invalidate a higher-level decision.

## Artifact Workflows

Artifact choice must not change the decision logic. It changes how the record is stored and reviewed.

### Google Sheets

Use Google Sheets when the user wants a visual, durable, collaborative TOYL-style decision framework.

Rules:

- Treat Google Sheets as an artifact setting, not an operating mode.
- Use the user's Google Sheets template, when they supply one, as the primary visual structure when the user asks to fill a real decision framework.
- Read spreadsheet metadata before reading or writing ranges.
- Confirm the relevant tab before meaningful edits.
- Preserve formulas. Write inputs, not calculated score cells, unless the user explicitly asks to repair formulas.
- Maintain the record while facilitating; do not wait until the end if the job is to fill the framework collaboratively.
- If the user asks to create a new Google Sheet from the template, copy or recreate the template structure before filling it, and report the new sheet link/id when available.
- If a connector, auth, or permission blocks live editing, produce a Markdown/XLSX-ready record and state the block.

### Excel / XLSX

Use Excel when the user asks for a local spreadsheet, Google Sheets is unavailable, or a local file should be created before import.

Rules:

- Preserve formulas where possible.
- Keep input sections aligned to the TOYL structure: decision/date, outcomes, options, option evaluations, comparison, mitigation, and commitment.
- If converting between Excel and Google Sheets, verify formulas and formatting after conversion when tool access permits.

### Markdown / Chat

Use Markdown or chat for autonomous runs, audits, facilitated records, and eligible decisions where spreadsheet editing is not requested.

Rules:

- Still include the same logical record sections.
- For audits, lead with findings and then show corrected sections.
- For autonomous runs, include assumptions, missing information, confidence, and reversal triggers.

## Autonomous QA And Delegation

Large autonomous runs are risky because the same agent may miss earlier errors when revising later sections. Use checkpoints to prevent shortcutting.

Preferred checkpoint gates:

1. Decision-object gate: confirm the request is priority, outcome-group definition, path-to-outcome, or execution.
2. Outcome-group gate: test definitions, AND relationships, missing stakeholder/constraint/standard items, and outcome/strategy mixing.
3. Option-space gate: test whether options are at the same abstraction level, include at least three viable options when possible, and need a MECE tree.
4. Inversion gate: test procedural failures, bias, tactic/strategy failures, owner fit, skill deficiencies, and unlivable downside risk.
5. Scoring gate: test impact/probability assumptions, score consistency, close calls, and sensitivity to one row.
6. Mitigation gate: test whether mitigations are real, required, too costly, or turn the path into a new option.
7. Artifact gate: test whether the record and formulas match the reasoning.

Use subagent checkpoints when the user asks for or authorizes them and the environment's tool policy permits them for the current task. If not using subagents, run the same list as explicit self-review before finalizing an autonomous recommendation.

## Revision Loops

Revision is required when new evidence changes a previous layer.

Loop triggers:

- The outcome group omits a consequence that actually matters.
- An option's major upside/downside is unrelated to any listed outcome, revealing an incomplete outcome group.
- The option set is not collectively exhaustive enough for the stakes.
- A concrete option is mixed with abstract categories as siblings.
- A downside or worst case is unlivable.
- A mitigation materially changes the option.
- Scores are close, unstable, or driven by one row.
- New execution information changes resources, results, constraints, risks, outcomes, or priority.

Loop rule: reopen the lowest layer that is invalidated, then update all downstream sections and artifacts. Do not keep stale scoring or conclusions after a loop.

## Model Inventory

Each model states its shape. Follow `$mece-thinking`: strict MECE is the default, and its narrow `~MECE` utility exception requires a concrete comparison. None of the models below is pre-approved for that exception. A partition needs one parent set, one unit, one level, and disjoint, exhaustive predicates. Decompose compound items before assigning them. A process or graph is not a partition. In a multi-axis model, define each axis separately and retain all applicable values; never choose a primary label to hide overlap. Use the defined unit and procedure when building the record, not just the model labels.

### Model 1: Company Decision-Object Taxonomy

Shape: MECE partition.

Parent set: all decisions that can be made by any person in a company. Unit: one atomic decision about one layer. Decompose requests that change more than one layer into linked decisions.

Buckets:

1. Company priority decision: decide which problem, opportunity, main outcome, or outcome group the company should solve or prioritize relative to other possible company goals.
2. Outcome-group definition decision: decide the exact group of outcomes that define success for the selected priority/problem/outcome.
3. Path-to-outcome decision: decide between ways, options, or strategies for reaching a defined outcome group.
4. Execution decision: decide what to do while executing a selected path, including whether new information means continue, adjust, pause, cancel, or reopen another decision object.

Assignment rule: classify the layer being decided, not when the question occurred. Priority is bucket 1; the success definition for a fixed priority is bucket 2; path selection for fixed success criteria is bucket 3; action within a fixed selected path is bucket 4. A decision to replace the path during execution is bucket 3, linked from execution triage. A compound decision keeps separate records for each affected layer.

### Model 2: Tony Worksheet Applicability

Shape: mapping from Model 1 buckets to allowed process depth.

Parent set: the four decision objects in Model 1.

Buckets:

1. Priority decision: Tony worksheet is not specified as the full method; only use general priority/80-20 reasoning if appropriate and state missing scoring rules.
2. Outcome-group definition decision: use Tony Step 1-style outcome definition plus MECE term/outcome clarification; do not force option scoring.
3. Path-to-outcome decision: use the full Tony worksheet process.
4. Execution decision: use local execution reasoning; use the full Tony process only if the execution question itself becomes a path-to-outcome decision, and reopen bucket 1/2/3 when new information invalidates that level.

Assignment rule: never apply more of the worksheet than the decision object justifies.

### Model 3: Reopen Routing Model

Shape: process/graph model.

Parent set: all cases where new execution information changes a previous decision basis.

Routes:

1. Execution-only adjustment: new information changes tactics but not the selected path, outcome group, or priority.
2. Reopen path-to-outcome decision: new information changes which path is best.
3. Reopen outcome-group definition: new information changes what success must mean.
4. Reopen company priority decision: new information changes whether this problem/outcome should be the company focus relative to other goals.

Routing rule: reopen the lowest decision object whose basis is invalidated; do not restart the whole model when a local execution decision is enough.

### Model 4: Outcome-Group Item Types

Shape: typed outcome record with a strict evaluation-mode partition and separate descriptive tags.

Parent set: atomic evaluation criteria in the decision's outcome group. Give each criterion an ID and an observable definition. Split a sentence if it contains several tests.

Evaluation-mode buckets:

1. Mandatory gate: a condition that must hold for an option to be acceptable. Define its pass predicate and required evidence. Main outcomes and co-required outcomes remain AND gates unless explicitly made preferences.
2. Graded preference: a condition whose degree of achievement helps rank otherwise acceptable options. Define its direction and scoring anchors; it cannot compensate for a failed mandatory gate.

Assignment rule: declare whether each criterion excludes options or ranks acceptable options. If a goal has both a required minimum and value above that minimum, record a minimum gate and a separate incremental preference. Link them and do not score the minimum twice. If the intended mode is unknown, expose that missing decision; do not infer it from a phrase such as “quality” or “budget.”

Preserve the original useful distinctions as tags or relationships: main outcome, independent co-required outcome, concern/risk control, downside avoidance, stakeholder/process, standard/quality, and constraint. Multiple tags can apply to one criterion. They are not competing buckets. Instrumental/enabling conditions are linked causal hypotheses in Model 5; make one an evaluation criterion only if its own satisfaction is required or valued, not merely because it is a proposed route to an outcome.

Break test: “Spend no more than 100,000” is one mandatory gate when that cap is binding. It may carry constraint and downside tags, but it gets one predicate and one gate result. “Lower cost is better” is a separate graded preference only if the decision calls for it.

### Model 5: Outcome Relationship Model

Shape: multi-axis check.

Parent set: relationships among items in a company decision's outcome group.

Relationship types:

1. AND relationship: all listed outcomes must be satisfied together.
2. Means-to-end relationship: one outcome item helps cause another.
3. Concern/avoidance relationship: an item exists to avoid a feared downside.
4. Stakeholder dependency relationship: involvement, trust, or buy-in affects success.
5. Constraint relationship: an item limits which paths are acceptable.
6. Standard relationship: an item defines the quality bar for satisfying another outcome.

Use rule: identify relationships before scoring so the same concern is not double-counted or mistaken for a strategy.

### Model 6: Term-Definition Model

Shape: definition procedure with a strict partition by the field containing each use.

Parent set: ambiguous term occurrences in the decision record. Unit: a term in one identified field, not the word across all contexts.

Record each occurrence under its field ID: problem/priority statement, outcome criterion, option description, stakeholder identity, consequence statement, scoring definition, or another explicitly named record field. One occurrence has one field location. Split a sentence that combines fields before classifying it.

Use rule: define the term where its ambiguity would change the decision. Link shared meanings across fields to one canonical definition. Preserve distinct meanings when warranted. For example, “risk” in a mandatory downside gate and “risk” in a probability estimate need separate definitions or an explicit relationship; a single primary-role label must not hide the difference. Constraints and standards are outcome-criterion tags from Model 4, not parallel term buckets.

### Model 7: Option-Generation Modes

Shape: process/source model.

Parent set: valid ways to create candidate paths/options for a path-to-outcome decision.

Modes:

1. Best-options brainstorm: list the strongest plausible options directly.
2. Full logical MECE option space: partition all categorically possible option classes.
3. Hybrid/fourth-option creation: create a new option revealed by scoring, mitigation, or combining strengths.

Use rule: brainstorm when options are obvious; use MECE when hidden categories, abstraction confusion, or strategic stakes make incompleteness risky. Regardless of mode, preserve Tony's rule: one option is no choice, two options is a dilemma, and at least three options is preferred when possible.

### Model 8: MECE Option-Tree Refinement

Shape: ordered process model.

Parent set: phases in deriving concrete viable options from a MECE option space.

Phases:

1. Define the abstract parent set: all possible ways to achieve the outcome group.
2. Split the parent set into same-level MECE categories.
3. Sub-MECE any abstract category that is still too broad to score.
4. Apply real requirements to eliminate nonviable branches.
5. Keep the concrete viable leaves as scoreable options.

Use rule: start with abstract categories only when useful, sub-MECE them one level at a time, eliminate branches that fail real requirements, and stop when the remaining leaves are concrete enough to score. Do not mix abstract categories and concrete choices as siblings.

### Model 9: Option Requirement/Filter Model

Shape: strict partition of gate results, followed by an option-level decision rule.

Parent set: results for every option × mandatory-gate pair from Model 4. Unit: one option tested against one gate predicate using the stated evidence.

Buckets:

1. Pass: the evidence establishes that the predicate is satisfied.
2. Fail: the evidence establishes that the predicate is not satisfied.
3. Unresolved: the evidence does not establish either result, including conflicting evidence or an undefined threshold.

Decision rule: any failed mandatory gate makes the option ineligible in its current form. If none fail but any are unresolved, label eligibility unresolved and identify the smallest useful check; do not treat missing evidence as a pass. If all pass, the option is eligible for preference scoring. Mitigation creates a refined option whose affected gates must be checked again.

Record every failed gate ID and its evidence once. Outcome, constraint, stakeholder/process, standard, and unacceptable-downside labels are tags from Model 4, not mutually exclusive rejection causes. An unknown requirement can remain a clearly stated assumption in an autonomous recommendation, but cannot support a claim of verified eligibility or authorize execution.

Break test: exceeding the binding 100,000 spending cap produces one failed gate with constraint/downside tags. It does not produce separate “outcome failure” and “constraint failure” rows. Another independently failed quality gate is recorded as well, rather than discarded by a primary-reason rule.

### Model 10: Consequence Model

Shape: scope check followed by a strict sign partition for atomic effects.

First check whether each material consequence is represented in the outcome group. If not, revise the outcome group or explain why the effect is outside the agreed decision scope. Do not label an unrepresented material effect irrelevant to preserve the current model.

Parent set for scoring: atomic consequence × affected graded-preference pairs, relative to one stated baseline and time horizon. Split mixed effects, outcomes, or time periods when they have different signs.

Buckets:

1. Upside: a positive change on that preference's defined scale.
2. Downside: a negative change on that scale.
3. Neutral: no change on that scale.

Assignment rule: record the sign for each pair. An unknown sign remains an unresolved estimate until researched or modeled as explicit scenarios; do not force it into a known sign. An option that improves speed but harms quality has two linked effects, not one primary label. Keep shared causes and overlapping value visible so they are not counted twice. Check mandatory-gate effects through Model 9 before allowing preference scores to decide.

### Model 11: Consequence Discovery Mode

Shape: process/source model.

Parent set: valid ways to discover upsides and downsides.

Modes:

1. Important-consequence brainstorming: default; list the important upsides/downsides the decision-maker can think of.
2. MECE consequence tree: use when the consequence set is complex, lopsided, duplicated, or likely missing a major class.

Use rule: do not force MECE if brainstorming captures the important consequences well enough; do use MECE when incompleteness would materially change the decision.

### Model 12: Evaluation Variables

Shape: equation/variable model.

Parent set: quantities used to evaluate consequences and option totals.

Variables:

1. Impact/importance: how good or bad the effect would be if it happened, scored on `0..10` (or `-10..+10` only for the explicit signed variant).
2. Probability/likelihood: how likely the effect is if the option is chosen, always expressed as a decimal on `0..1` (for example, `0.8`, never `8`).
3. Expected score contribution: impact multiplied by probability on the chosen utility scale.
4. Option total: upside expected effects minus downside expected effects, or signed expected effects summed consistently.

Use rule: use one scoring method consistently. Define shared impact anchors across outcomes and options, avoid duplicate or overlapping value, and show sensitivity when plausible estimates change the ranking. These subjective scores are a decision aid, not measured monetary expected value or objective precision. Multiplication does not make an arbitrary ordinal rating a calibrated utility scale. If comparable impact differences cannot be defended, use qualitative comparisons instead of a decisive total. The canonical separate-row method uses `0..10` importance and `0..1` decimal probability. Calculate, for example, `8 * 0.8 = 6.4`. Never encode probability as an integer `0..10`; normalize a legacy value such as `8` to `0.8` before scoring. The spoken source also mentioned a possible signed `-10..+10` impact scale; use that only when chosen explicitly, while probability remains `0..1`.

### Model 13: Inversion Timing

Shape: ordered process model.

Parent set: moments when "How can this decision be messed up?" can be asked.

Moments:

1. After outcome group definition, because the decision is only clear once outcomes are clear.
2. After option generation, because options reveal additional ways to mess up and can force option swaps.
3. During execution, because new resources, results, constraints, or risks can invalidate previous decisions.

Use rule: run inversion after outcome definition and again after options when needed.

### Model 14: Inversion Failure-Type Taxonomy

Shape: causal failure graph with a strict partition by the location of each atomic failed condition.

Parent set: identified conditions that could prevent the decision from achieving its outcome group. Unit: one failed condition at one location; separate a causal chain into linked conditions.

Buckets:

1. Decision-record condition: the analysis or choice is defective, such as missing evidence, unclear terms, omitted options, or incorrect scoring.
2. Selected-plan condition: the plan as specified cannot meet a requirement, such as an infeasible tactic, inadequate owner capability, or missing mitigation.
3. Execution condition: actual action differs from the selected plan or its required operating conditions, such as an omitted step or an unhandled external change.

Assignment rule: identify what is defective at each location. A biased estimate that leads to an infeasible tactic is two linked conditions in buckets 1 and 2. Bias, incentives, procedural defects, and stakeholder issues remain cause tags that can apply at several locations. Record those causes and their mitigations; do not force a single primary cause or discard links. If a proposed condition cannot be located, clarify or decompose it before claiming this partition covers it.

### Model 15: Owner/Leader Fit Failure Model

Shape: multi-axis failure check.

Parent set: ways an assigned person can make an option fail.

Failure types:

1. Bias/incentive mismatch: the person is biased toward a silo, pet solution, or local optimum.
2. Cross-functional leadership gap: the person lacks skill leading across the required silos or people.
3. Silo-knowledge gap: the person does not know, and cannot readily access, all relevant silos.
4. Standard mismatch: the person is good enough in a normal sense but below the required 80/20, top-percentile, or top-1-percent standard for the outcome.

Use rule: apply when an option depends on assigning, hiring, empowering, or trusting a person.

### Model 16: Skill-Deficiency Model

Shape: capability-gap record with two strict assessment axes and descriptive nature tags.

Parent set: atomic capability gaps relevant to a specific role and outcome. Define the capability, required level, evidence, decision horizon, and available compensation before classification.

Nature tags: technical/procedural, interpersonal/behavioral, and domain/context/silo knowledge. Several tags can apply; these are not a partition and do not substitute for a concrete capability description.

Axis A - feasibility inside the decision horizon:

1. Resolvable: evidence supports an available teaching, support, or compensation path that meets the required level by the deadline.
2. Not resolvable: evidence rules out the available paths under the stated constraints.
3. Unresolved: the evidence does not establish either conclusion.

Record estimated time and cost directly. Do not use undefined “fast” and “slow” buckets.

Axis B - outcome effect under the proposed plan:

1. Limiting: the gap prevents a required outcome or materially limits a graded preference under explicit assumptions.
2. Non-limiting: the gap does not have that effect under those assumptions.
3. Unresolved: the effect cannot yet be established.

Use rule: compare concrete limiting gaps, feasible compensation, and the cost of delay. Several gaps can be limiting. Do not infer permanent traits or select a person from a general label.

### Model 17: Unacceptable Downside Filter

Shape: MECE partition.

Parent set: downside/worst-case profiles for an option.

Buckets:

1. Livable downside: the current profile is within the defined acceptance boundary.
2. Mitigatable unlivable downside: the current profile is outside that boundary, but a specific feasible mitigation can bring it inside. Evaluate the refined option before accepting it.
3. Unlivable downside: the current profile is outside that boundary and no feasible mitigation within scope can bring it inside.

These buckets apply once acceptability and mitigation feasibility are established. If either is unknown, report an unresolved assessment and the missing fact; do not label it livable.

Assignment rule: if the company or decision-maker cannot live with the downside or worst case, remove the option no matter how unlikely it seems.

### Model 18: Mitigation Generation Mode

Shape: process/source model.

Parent set: valid ways to reduce the chosen option's key downsides.

Modes:

1. Creative brainstorm mitigation: default mode.
2. MECE mitigation tree: use when the downside space is complex or hidden.
3. New/refined option: mitigation changes the path enough to become a new option that must be scored.

Use rule: brainstorm first unless the downside space itself needs MECE clarity.

### Model 19: Execution New-Information Model

Shape: change-impact graph followed by a strict decision-layer partition.

Parent set: atomic changes to the basis of a selected path. Record each observed change once with its source, previous state, new state, and confidence. Split compound observations into linked facts.

Discovery facets: resources; actual results; external or internal constraints; likelihood or severity of downside; and desired outcomes or priorities. Check all relevant facets. These can overlap: losing a required license changes authority, a constraint, and risk. Retain those links rather than choosing a primary information type.

For each changed fact, test its effect on each fixed layer from Model 1: priority, outcome definition, path, and execution action. Record each fact × layer result as invalidated, still supported, or unresolved. Route every invalidated layer through Model 3 and update dependent records. If a higher layer changes, resolve that basis before making dependent path or execution choices.

Break test: a budget reduction is one sourced fact. It may invalidate the selected path while leaving the priority intact. Record both assessments; do not force the fact into either a resource or constraint bucket, and do not restart priority analysis without evidence that priority changed.

## Branch Workflows

### Branch 1: Company Priority Decision

Use for deciding which company problem, opportunity, main outcome, or outcome group to prioritize relative to other company goals.

What is specified:

- This is a real decision object in itself.
- It happens at a general/meta company level.
- It may later feed into outcome-group definition.

What is not fully specified:

- The complete scoring system for comparing all company priorities.

Default behavior:

- Define the candidate parent set of company problems/outcomes.
- If the user asks for leverage or 80/20 priority reasoning, load `$8020-thinking`; otherwise state that priority scoring is not fully specified here.
- Do not pretend the Tony worksheet fully solves this branch unless the priority question is converted into a path-like option choice with explicit outcomes.

### Branch 2: Outcome-Group Definition Decision

Use for deciding what success must mean before comparing paths.

Workflow:

1. Define the main outcome/problem.
2. List outcome-group items in order of importance.
3. Treat items as AND relationships by default.
4. Define key terms.
5. Classify outcome-group items using Models 4 and 5.
6. Recast strategies into outcomes, requirements, or mitigations when needed.
7. Run inversion after the outcome group is clear.

### Branch 3: Path-To-Outcome Decision

Use the full Tony-style process:

1. Outcomes: confirm the outcome group.
2. Options: generate at least three real options when possible.
3. Consequences: check every mandatory gate using Model 9, then record atomic preference effects using Model 10.
4. Evaluation: use Model 12 to score comparable effects for eligible options, or make a qualitative comparison when the scale cannot support a meaningful total.
5. Mitigation: choose the best option so far, then reduce key downsides.
6. Resolve: commit to the option with the best expected outcome after unacceptable downside filtering and mitigation.

If scoring reveals a missing option, add it and run the same process.

### Branch 4: Execution Decision

Use for decisions while executing a selected path.

Workflow:

1. Identify the new information, if any.
2. Classify it using Model 19.
3. Decide whether it affects only execution tactics or invalidates a higher decision object.
4. Continue, adjust, pause, cancel, or reopen Branch 3/2/1 as appropriate.

Do not reopen higher levels just because execution is difficult. Reopen only when new information changes expected outcome, feasibility, unacceptable downside, or priority basis enough to matter.

## Detailed Tony Path Process

### Outcomes

Use the outcome group as the standard for all later evaluation. Upsides and downsides are only meaningful relative to this group.

Ask:

- What do we want to happen?
- Why does each outcome matter?
- Which outcomes are required together?
- Which items are concerns, avoidance requirements, stakeholder requirements, or standards?
- Which terms need definitions?

### Options

Use at least three real options when possible.

For brainstorm mode, ask for obvious, bolder, lower-risk, current-path, and hybrid options.

For MECE mode:

1. Define the parent set: all possible ways to achieve the outcome group.
2. Pick one split basis at a time.
3. Make sibling categories mutually exclusive and collectively exhaustive.
4. Drill down through sub-MECE categories.
5. Apply requirements and filters.
6. Stop at concrete viable choices.

### Consequences And Evaluation

For each option:

- List upsides and downsides relative to the outcome group.
- Check mandatory gates first using Model 9; retain unresolved eligibility rather than assuming a pass.
- Split scored effects by affected graded preference using Model 10.
- Score impact/importance using Model 12's shared anchors and duplicate-value check.
- Score probability as a decimal from `0` to `1` (for example, `0.8`, not `8`).
- Compute expected effect.
- Sum the option total.

Use scoring to expose assumptions, not to create fake precision. If scores are close or driven by one row, inspect sensitivity.

### Inversion

Prompt: "How can this decision be messed up?"

Run it:

- After the outcome group is defined.
- After options are drafted if options reveal more risks.
- During execution when new information appears.

Convert serious inversion findings into non-negotiables, filters, mitigations, new options, owner requirements, or reasons to reopen a prior branch.

### Unacceptable Downside

For each option ask:

"Can the company/decision-maker live with this downside or worst case?"

If no, remove the option regardless of probability. If mitigation changes the downside enough to make it livable, treat the mitigated path as a refined/new option.

### Mitigation

After the best option so far:

1. List its key downsides.
2. Brainstorm ways to reduce them.
3. Decide whether each mitigation is required, optional, or too costly.
4. Re-score if the mitigation materially changes the option.

### Resolve

Finish with:

- Final choice.
- Why it best satisfies the outcome group.
- Why rejected options lost.
- Remaining risks.
- Required mitigations.
- First action today.
- Owner.
- Commitment date.
- Review trigger when useful.

## Sheet-Filling Notes

When filling a Google Sheets decision template:

- Read metadata before ranges.
- Use the decision tab that the metadata confirms.
- Treat sheet filling as the artifact workflow inside facilitated, autonomous, or audit mode.
- Fill decision/date first.
- Fill outcomes and purposes in priority order.
- Fill three options when possible.
- Keep mandatory-gate results visible in an available notes field or accompanying record; a net score must not hide a failed or unresolved gate.
- Fill upsides, downsides, affected preferences, importance, and probability using Models 10 and 12. Enter probability as a decimal on `0..1`; if the sheet only accepts `0..10`, flag the template mismatch and continue the analysis in an explicit compatible record. Do not silently change the sheet's scale or overwrite its formulas.
- Let formulas calculate scores unless the template has changed.
- Compare net scores.
- Fill best option, mitigation rows, and commitment fields.
- In facilitated mode, fill as the decision develops and checkpoint uncertain judgment calls with the user.
- In autonomous mode, fill assumptions and missing information visibly instead of hiding them.
- In audit mode, preserve original values unless the user asks for fixes; when fixing, keep a clear change trail in the response.
- Do not overwrite formulas unless explicitly asked.

## Common Mistakes To Prevent

- Comparing options against different outcome groups.
- Forcing MECE where important-consequence brainstorming is enough.

## Skill-Meta Guard

This guard is about using the skill, not about the company-decision ontology.

Classify any process rule in this skill as:

1. Specified rule: directly stated by the user or the provided Tony/template sources.
2. Partially specified rule: partly stated, but some criteria or scoring mechanics are missing.
3. Unspecified rule: not provided yet.

Only present specified rules as firm. Mark partial or missing rules before using assumptions.
