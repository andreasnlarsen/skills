# Code Quality & Structure

---

## CQ-01: File Sizes

**What:** A large source file may combine responsibilities that are difficult to understand or change.
**Detection:** static — count non-blank, non-comment lines per file.
**Possible correction:** Extract a bounded responsibility only when it makes a demonstrated change or verification problem more local.

## CQ-02: Function Sizes

**What:** A long function may obscure a responsibility, decision or control-flow boundary.
**Detection:** static — count lines per function/method definition.
**Possible correction:** Extract a coherent responsibility or name an intermediate operation when that makes the function easier to change; length alone does not require helpers.

## CQ-03: Cyclomatic Complexity

**What:** Functions with deeply branching logic (many if/else/switch paths).
**Detection:** static — count branching statements (if, else if, case, &&, ||, ternary) per function.
**Possible correction:** Use guard clauses, named predicates or a state model when they make the actual decisions clearer.

## CQ-04: Nesting Depth

**What:** Deeply nested code blocks (if inside if inside loop inside try).
**Detection:** static — measure maximum indentation depth per function.
**Possible correction:** Use early returns or extract inner blocks when nesting hides control flow; preserve ordering, cleanup and error behavior.

## CQ-05: Dead Code

**What:** Unused exports, unreachable code, commented-out blocks.
**Detection:** static — trace unused exports and unreachable code, and inspect commented-out implementation against dynamic/external callers and useful documentation. Existing lint results can identify candidates.
**Possible correction:** Delete code with no static, dynamic or external caller (git preserves history); retain useful examples and migration context.

## CQ-06: Code Duplication

**What:** Near-identical logic blocks across files, or the same business knowledge implemented independently in paths that must change together.
**Detection:** static — look for similar function signatures and repeated patterns across files, then establish whether they express the same rule or separate concepts.
**Possible correction:** Consolidate duplicated business knowledge at its domain owner when those paths must change together; similar syntax for different concepts can remain local.

When duplicated blocks encode the same business decision, inspect whether a supported change can make them disagree. Similar syntax alone is not duplicated business knowledge.

## CQ-07: Circular Dependencies

**What:** Module A imports B, B imports A (directly or transitively).
**Detection:** static — trace import chains. Dynamic — `madge --circular` (JS/TS), or equivalent.
**Possible correction:** Extract shared types or move responsibility to break the cycle when it causes an initialization failure or changeability problem.

## CQ-08: Naming Consistency

**What:** Inconsistent naming conventions across the codebase.
**Detection:** static — check for mixed camelCase/snake_case in same language, inconsistent file naming (UserService.ts vs user-service.ts), inconsistent boolean naming (isReady vs ready vs hasReady).
**Possible correction:** Align misleading names with the existing domain vocabulary; preserve intentional language or external naming differences.

## CQ-09: God Files/Classes

**What:** Single files or classes that handle too many responsibilities.
**Detection:** static — trace the distinct responsibilities, consumers and reasons for change in a file or class. Size and fan-in can select candidates but do not establish poor cohesion.
**Possible correction:** Split by domain concept when independent changes interfere; keep a cohesive implementation together even with many methods.

## CQ-10: TODO/FIXME Density

**What:** Accumulated TODO/FIXME/HACK/XXX comments indicating deferred work.
**Detection:** static — grep for TODO, FIXME, HACK, XXX patterns.
**Possible correction:** Convert actionable TODOs to tracked work or fix them; retain useful context, since age and count alone do not decide removal.

## CQ-11: Magic Numbers/Strings

**What:** An unexplained value hides domain meaning or is copied where a shared rule must change consistently.
**Detection:** static — inspect literals in relevant decisions and calculations for unclear meaning, duplicated knowledge or environment dependence.
**Possible correction:** Extract named constants when a value's meaning or shared change policy is unclear; keep obvious local literals local.

## CQ-12: Inconsistent Error Handling

**What:** Failure behavior is unclear or inconsistent at a caller boundary.
**Detection:** static — look for mixed patterns: empty catch blocks, swallowed errors (`catch(e) {}`), inconsistent error return types.
**Possible correction:** Standardize failure behavior at the affected caller boundary with a shared error type when callers cannot tell outcomes apart; never swallow errors silently.

## CQ-13: Module Cohesion

See [CQ-15](checks-code-quality.md#cq-15-catch-all-shared-modules-owning-domain-logic).

## CQ-14: Ownerless Domain Logic

**What:** Shared business logic exists, but no canonical module or service is clearly responsible for it.
**Detection:** static — trace a business rule across handlers, jobs, hooks, or helpers and check whether one module is the obvious source of truth. Look for multiple writers/readers implementing the same decision locally.
**Possible correction:** Name a canonical owner, move the rule there and hard-cut in-scope callers over; document a justified runtime or contract exception.

## CQ-15: Catch-All Shared Modules Owning Domain Logic

**What:** A generic shared module such as `utils`, `helpers`, `common`, or `misc` owns real business logic instead of narrow reusable primitives.
**Detection:** static — inspect catch-all modules for pricing, permissions, eligibility, status logic, query shaping, or domain-specific data transformation.
**Possible correction:** Move each business rule to a named owner when the catch-all grouping causes coupling; leave only generic primitives behind.

## CQ-16: Split Authority / Multiple Mutators

**What:** Multiple in-scope paths are allowed to mutate the same shared mutable business state or finalize the same durable side effect, so the system effectively has co-equal authorities.
**Detection:** static — map the state or side effect, its system of record, every mutating/finalizing path, and the authoritative mutator. Check handlers, webhooks, jobs, workers, hooks, return pages, and recovery flows. See [split-authority-patterns.md](split-authority-patterns.md).
**Possible correction:** Name one authoritative mutator and system of record; cut other paths over to read, display, enqueue or projection roles.

## CQ-17: API Surface Area

**What:** An exposed API surface makes unrelated changes propagate or allows callers to depend on internals.
**Detection:** static — count public exports per module. Check for `export *` patterns.
**Possible correction:** Export only what consumers need when a surface exposes internals or propagates changes; barrel files are an organizational option.

## CQ-18: Implicit Lifecycle Rules

**What:** Current state affects what happens next, and the rules have to be inferred from fields, flags, conditions or separate entry points. A named status field or a single writer can still hide implicit transition rules.

**Detection:** Trace state-dependent workflows across the applicable UI, APIs, persistence, jobs and webhooks. Cite the code that supports each transition and record its source and destination states, trigger, conditions, finalizing path and material side effects. Separate current behavior from requirements. Report what you inspected and where reachability or coverage is uncertain.

**Possible correction:** When a supported failure or demonstrated change cost warrants it, recommend the smallest code change that makes the rule explicit. Name the intended transition or rejection, the owner that should enforce it, affected callers and a check that would establish the result. A guard in the existing owner may be enough. Consider named states or a transition table when they clarify the rules. Keep independent state dimensions separate.
