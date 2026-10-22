# AGENTS.md

This repo holds my own agent skills, installed into other projects with the [`skills`](https://skills.sh) CLI (see [README.md](./README.md)).

## Skills

- **Each skill lives in its own folder under `skills/`**: `skills/<name>/SKILL.md`, its `agents/openai.yaml`, and any reference files the skill discloses.
- **Before creating or editing a skill, or this file, call the Skill tool with "writing-for-agents".**
- **Every skill in `skills/` has an entry in [README.md](./README.md)** under **Model-invoked** or **User-invoked**, with the skill name linked to its `SKILL.md`.
- **A skill is user-invoked in both `SKILL.md` and `agents/openai.yaml`, or in neither.** [.agents/invocation.md](./.agents/invocation.md) holds the rule, and how one skill calls another (through the Skill tool, never a link into another skill's folder).

## Installed skills

`.agents/skills/` holds third-party skills used while writing these, installed with `npx skills add`, recorded in [`skills-lock.json`](./skills-lock.json) and symlinked into `.claude/skills/`.

- **Never edit a skill listed in `skills-lock.json`**: it is installed from an external source, so a hand edit is lost on the next `npx skills update`. Raise a needed behaviour change with the user.
- **Keep `skills-lock.json` committed.** When someone installs from this repo, the CLI skips every skill the lock file lists, so the third-party skills never show up as ours.

## Writing

- **No em-dashes anywhere in this repo's prose.** Where a sentence reaches for one, rewrite it with a comma, colon, period, parentheses or a conjunction, whichever the sentence wants.
- **Each file opens by saying what it is for**: a skill's frontmatter `description`, a doc's first paragraph, a script's top comment.
