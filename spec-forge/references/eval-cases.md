# Eval cases

Past failures kept as test cases for this skill. These are not instructions; use them when testing or maintaining the skill.

## Goal created from an accepted native implementation prompt
- Situation: The user accepted the client's native implementation prompt after a plan; no Goal was requested.
- Wrong behavior: The agent treated that acceptance as a Goal request and expanded its authority past the user checkpoint.
- Expected behavior: A Goal needs an explicit request in the continuous task; accepting an implementation prompt is not one, and the design checkpoint still applies.

## Accepted spec renumbered to match the template
- Situation: An accepted spec with established requirement IDs was refined using the optional spec template.
- Wrong behavior: The agent renumbered existing requirements to fit the template's ordering.
- Expected behavior: Preserve existing IDs, names, priorities and scope; add IDs only for new requirements.
