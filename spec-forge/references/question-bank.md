# Question Bank

Use stage dependencies before regret ranking. During UI planning, use [frontend-planning.md](frontend-planning.md): ask now if a wrong assumption could invalidate the next artifact, regardless of whether it concerns frontend, backend, or data. Park other details with the stage that must resolve them. Questions below are ordered by expected regret within each section. Ask only applicable questions not already answered by context or inspection, with the highest-regret gaps first. This is a selection bank, not a required interview script.

Consider these factors qualitatively when selecting a material gap; no scoring calculation is required:
- Impact: How much does a wrong answer cost?
- Irreversibility: How hard to change later?
- Uncertainty: How likely is the answer surprising?
- DependencyDegree: How many downstream decisions depend on this?

---

## Goal & Scope (establish first — everything depends on this)

1. **What problem are you solving, and for whom?** (Impact: high, Irreversibility: high, DependencyDegree: everything)
2. **What does success look like in 1 month? 6 months?** (Grounds the scope)
3. **What should this project explicitly NOT do?** (Prevents scope creep early)
4. **Is there an existing product/tool that almost solves this? Why isn't it enough?** (Build vs buy signal)

## Target Users

5. **Who is the primary user? Describe a specific person.** (Anchors all UX decisions)
6. **Are there secondary users with different needs?** (May split requirements)
7. **What's the user's current workflow without this tool?** (Reveals the pain point)

## Requirements & Priorities

8. **What's the one feature that, if missing, makes the whole thing pointless?** (P0 anchor)
9. **What would you cut if you had to ship in half the time?** (Separates P0 from P1)
10. **What evidence would establish the required outcome?** (Propose checks from the requirement and existing project evidence first; ask only about a material decision the user must supply.)
11. **Are there regulatory, compliance, or legal requirements?** (High irreversibility if missed)

## Build vs Buy (open or materially changed choices only)

Reuse settled choices unless new evidence or the requested change makes them material again. Inspect existing capability before asking these questions.

12. **Does this need authentication? What kind?** (Commodity problem #1)
13. **Does this need payments or billing?** (Commodity problem #2)
14. **Does this need file uploads, search, or real-time features?** (Commodity problems #3-5)
15. **For an unresolved capability choice, is there a material build-versus-service constraint or preference?** (Do not reopen accepted architecture merely because the capability is common.)
16. **Are there cost constraints that affect buy decisions?** (Sometimes build is cheaper at scale)
16A. **Which choice keeps the next likely change cheaper: building here, or buying a service/library with lower maintenance burden?** (Avoids choosing based only on capability coverage)

## Architecture & Tech Stack

17. **Is the tech stack already decided, or open for discussion?** (Constraint vs. decision)
18. **Is this a new project or changes to an existing codebase?** (Completely changes approach)
19. **If existing codebase: what patterns/frameworks are already in use?** (Must follow existing conventions)
20. **Does this need a backend API, or is it frontend-only?** (Architecture fork)
21. **Where will this be deployed? Any infrastructure constraints?** (Irreversible if wrong)
21A. **What is the next likely change after MVP?** (Lets architecture optimize for the next real change rather than a hypothetical platform)
21B. **Where is the future shape genuinely unclear enough that we should prefer a replaceable seam over a "flexible" abstraction?** (Prevents speculative design)
21C. **What failures or degraded conditions are real enough to plan for now, and which ones should fail explicitly instead of getting a fallback path?** (Prevents speculative fallback behavior)

## Lifecycle / State Model

21D. **What are the core lifecycle objects or processes here?** (Makes stateful behavior explicit instead of hiding it in prose)
21E. **What states does each lifecycle object actually have, at one abstraction level?** (If states overlap or mix levels, invoke [$mece-thinking](../../mece-thinking/SKILL.md) before finalizing the model)
21F. **What transitions are allowed, and which transitions are forbidden or invalid?** (Prevents hidden or contradictory workflow rules)
21G. **What triggers each transition, and which path is authoritative for finalizing it?** (Names the real owner instead of leaving split authority implicit)
21H. **Which transitions or side effects must be idempotent?** (Critical for retries, jobs, webhooks, and external events)
21I. **What read/display paths must remain observational or non-authoritative even though they show the current state?** (Protects against accidental second writers/finalizers)
21J. **What recovery, retry, or reconciliation paths exist, and which of those are authoritative versus observational?** (Keeps recovery logic explicit without creating duplicate owners)

## Domain Vocabulary

21K. **What terms are canonical for the core concepts, states, and user-visible behaviors in this project?** (Prevents naming drift between spec and implementation)
21L. **Are there existing terms in the codebase or product language we should preserve even if alternatives sound cleaner?** (Avoids accidental re-vocabulary)

## Testing & Code Quality

22. **Does this project have an existing test suite? What framework?** (Inspect the project first. New test setup is needed only when the requested verification requires it.)
23. **Which existing checks exercise the affected behavior and realistic failures?** (Inspect first; a missing corresponding test file or coverage percentage does not establish a behavioral gap.)
24. **Does affected ownership, coupling or a verification gap threaten this change?** (Inspect the relevant code and callers first. Record material risks and only the response the requested outcome needs; file size alone does not require refactoring or a formal deferral.)
25. **Testing philosophy: TDD (test-first), test-alongside, or test-after?** (Preserve an explicit choice or project convention. Use a practical failing regression check for reproducible bugs; do not impose a blanket P0 cadence.)

## Data Model

26. **What are the core entities? How do they relate?** (Foundation of backend)
27. **Is there existing data that needs to be migrated?** (High irreversibility)
28. **What's the expected data volume?** (Affects storage/query decisions)

## Design & UI

29. **Does this project have a UI? Web, mobile, or CLI?** (Frontend vs. backend classification)
30. **Any existing brand guidelines, colors, or design language?** (Constraint)
31. **Do you have mockups, wireframes, or reference designs, and which decisions are accepted?** (Inspect supplied artifacts first; distinguish accepted journeys/states from suggestions and simulated behavior.)
32. **What's the responsive strategy? Desktop-first, mobile-first, or both?** (Affects implementation)

## Integrations

33. **What external services/APIs does this need to connect to?** (Dependency mapping)
34. **Are there rate limits, auth requirements, or cost concerns for integrations?** (Constraint discovery)
35. **Do integrations need to work offline or with degraded connectivity?** (Architecture impact)

## Non-Functional Requirements

36. **What latency is acceptable for the main user action?** (Performance target)
37. **How many concurrent users should this handle at launch? In 6 months?** (Scaling target)
38. **What's the uptime requirement?** (Reliability target — affects architecture)
39. **Are there security requirements beyond standard best practices?** (Compliance, audit trails)

## MVP & Milestones

40. **What's the deadline for MVP?** (Scoping constraint)
41. **Is this a one-person project or a team effort?** (Affects scope realism)
42. **What's the smallest thing you could ship and learn from?** (MVP anchor)

## Risks

43. **What's the biggest technical risk?** (What might not work)
44. **What's the biggest product risk?** (What might not matter)
45. **What would make you abandon this project?** (Kill criteria — surprisingly clarifying)

---

## "You Decide" Handling

Explicit delegation is an answer. Inspect the project and relevant current sources, then choose a suitable in-scope option. Preserve established decisions and prefer a reversible choice where evidence is incomplete. Record material defaults with their rationale; do not send the same options back to the user solely because a decision has high impact.

Ask when the missing information is a business fact or product decision that cannot safely be inferred, an essential user-owned design checkpoint, or authority for an action outside the current task. A technical tradeoff is not automatically such a boundary. Continue work that does not depend on the answer.

For example, an existing stack normally resolves the framework choice. A delegated greenfield storage choice can be researched and decided. An unknown refund entitlement or permission to use real customer data must not be invented as a technical default.
