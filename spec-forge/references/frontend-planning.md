# Frontend and Production Planning

Spec-forge owns requirements and stage transitions. The design workflow that builds the mockup (for example a Claude Desktop design session) owns mockup execution, turn-taking, page reviews and the single mockup handoff.

## Plan the Next Useful Artifact

Use the current brief, plan, source material, code and accepted decisions. Preserve backend and operational requirements even when the next artifact is a mockup. Propose JTBDs and journeys from those inputs. For SaaS, apps and internal tools, design around complete user tasks and include that principle in the design handoff.

Choose prototype-first for substantial unsettled UX. Use direct implementation planning for backend-only work, small defined UI changes, an accepted design or an explicit skip-mockup instruction. Screen counts do not determine the route.

Resolve a fact now when a wrong assumption could invalidate the next artifact. Data access, permissions, calculations, lifecycle states, latency and integration limits may determine what the UI can credibly show or do. Keep other unknowns with their resolution stage. Preserve source distinctions that affect roles, actions or completion; an agent's generalized mapping is not automatically a source fact or user decision.

## Prototype Plan and Execution

In native Plan mode, produce the required native output. A decision-complete prototype plan identifies its journeys/states, representative data and simulation boundaries, technical constraints, artifact location, Claude Desktop route, verification owner and user iteration/approval checkpoint. Retain an existing broader spec; backend implementation is not part of the prototype merely because backend constraints informed it.

Once execution is authorized, use the design workflow's Claude Desktop route. The frontend prototype demonstrates agreed sample-data behavior without production backend work or real external actions.

Use the design workflow's existing mockup handoff file (for example `mockup-handoff.md`). It owns actual output paths/revision, accepted decisions, simulations, pending work and evidence. Reconcile from the current files and that handoff; the design workflow owns retrieval of missing decisions from the same native Code conversation. Do not create a second handoff or ask the user to copy the conversation by default. A render or file change does not establish user approval.

## Page Review Return

“Page review mode” enters or resumes the design workflow's page and flow subreviews. Keep the parent spec-forge stage, active requirements path and return checkpoint in its existing handoff. Resume from that checkpoint rather than restarting discovery.

The design workflow owns page ordering, alternatives, user decisions, same-session implementation and verification. Ending a page or the page-review mode does not approve the whole mockup. On return, use the actual user approval and current artifacts to decide the next stage; a completed page queue is insufficient.

## Reconcile Production

After whole-mockup approval, compare the accepted artifact with the existing production plan in both directions: the real data, rules, permissions, transitions and integrations must support the accepted UI, and the UI must reflect those constraints. Distinguish simulation from real persistence, authorization and integration behavior.

Use another native Plan pass when material product/technical decisions changed or the user requested it. At that whole-mockup checkpoint, tell the user to return to this same Codex task, enter Plan mode and say **“Mockup approved. Plan implementation.”** The user can include any final corrections. Do not give this whole-product handoff after an individual page review or claim automatic mode changes/resumption from another app.

If the production plan remains decision-complete and differences are routine presentation details, reconcile them during existing authorized execution without adding a Plan pass. Explicitly delegated final design supplies the acceptance basis only within that delegation; do not invent user approval.

The production plan connects visible data/actions and critical journeys to real requirements, dependencies, verifiable phases and the requested finish line, including final rendered integration. Native Plan output remains the artifact while in Plan mode. Materialize or update the established requirements file during execution only when needed; that does not create another approval round.
