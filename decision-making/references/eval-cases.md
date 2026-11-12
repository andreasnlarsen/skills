# Eval cases

Past failures kept as test cases for this skill. These are not instructions; use them when testing or maintaining the skill.

## Template residue read as method
- Situation: The Google Sheets decision template contained leftover example values from an earlier use.
- Wrong behavior: The agent treated the residue as part of the decision method and carried it into the new record.
- Expected behavior: Use the template's structure and formulas; ignore accidental residue and report it if it blocks a clean record.
