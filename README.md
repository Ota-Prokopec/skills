# Skills

Small, composable instructions for Claude Code, Codex and any other agent that reads the [Agent Skills](https://agentskills.io) format.

Recommended to use with [Matt Pocock skills](https://github.com/mattpocock/skills).

## Install

Install a skill into a project with the [`skills`](https://skills.sh) CLI:

```bash
npx skills add Ota-Prokopec/skills --skill <name>
```

Update installed skills with `npx skills update`.

## Skills

### Model-invoked

The agent reaches for these when a task fits, and you can type them too.

- [prototype-code](skills/prototype-code/SKILL.md): write throwaway variants of the same code side by side, compare them, then use the one you pick.

### User-invoked

Only you can start these, by typing `/<name>`.
