# Skills for AI agents

Skills I use with Claude Code and Codex, shared as they are. Each folder is one skill: a `SKILL.md` and the reference files it reads.

| Skill | What it does |
| --- | --- |
| [spec-forge](spec-forge) | Interviews you, then writes the spec. |
| [review-and-autofix](review-and-autofix) | Reviews a code change, fixes what it finds, checks the fix. |
| [arch-health](arch-health) | Audits a codebase for how hard it is to change. |
| [pragmatic-programmer](pragmatic-programmer) | Finds the root cause before it fixes anything. |
| [mece-thinking](mece-thinking) | Splits a problem into parts that don't overlap and leave nothing out. |
| [decision-making](decision-making) | A written process for decisions that matter. |
| [8020-thinking](8020-thinking) | Finds the few things that give most of the result. |
| [musk-algorithm](musk-algorithm) | Question, delete, simplify, accelerate, automate. In that order. |

## Install

Copy a skill's folder into your agent's skills folder, keeping the folder name.

- Claude Code: `~/.claude/skills/` for every project, or `.claude/skills/` inside one project.
- Codex: `~/.codex/skills/`.

For example, for one skill in Claude Code:

```sh
git clone https://github.com/andreasnlarsen/skills.git
cp -R skills/mece-thinking ~/.claude/skills/
```

Some skills point to each other with relative links, so they work best installed side by side.

## Where they come from

These are cleaned copies of skills from my own setup. Names, paths and details from my own work have been taken out. `8020-thinking`, `musk-algorithm` and `pragmatic-programmer` are built on published books and interviews; they summarize, and the sources are named inside each skill.

More of what I make is at [apps.andreaslar.com](https://apps.andreaslar.com).

## Licence

[MIT](LICENSE).
