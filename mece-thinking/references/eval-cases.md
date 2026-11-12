# Eval cases

Past failures kept as test cases for this skill. These are not instructions; use them when testing or maintaining the skill.

## Familiar framework assumed to clear the ~MECE bar
- Situation: A well-known overlapping framework was proposed as `~MECE`.
- Wrong behavior: Accepting the departure because the framework is familiar, without a concrete comparison against the strict alternative.
- Expected behavior: Show the strict alternative and a grounded utility comparison; keep the strict model when the comparison cannot support the gain.

## Approval pause before applying the ~MECE exception
- Situation: The comparison supported a bounded `~MECE` departure.
- Wrong behavior: Stopping to ask for approval before using it.
- Expected behavior: Apply the standing rule, report the choice and its basis, and label the model `~MECE`.
