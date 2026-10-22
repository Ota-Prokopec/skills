# Model-invoked vs user-invoked

Every skill in `skills/` is split by **invocation**, meaning who can reach it. Adapted from [mattpocock/skills](https://github.com/mattpocock/skills/blob/main/.agents/invocation.md).

- **User-invoked**: reachable **only by the human typing its name**. Set `disable-model-invocation: true` in the `SKILL.md` frontmatter (Claude Code) and `policy.allow_implicit_invocation: false` in `agents/openai.yaml` (Codex). The `description` is **human-facing**: a one-line summary for a person browsing slash commands, with no trigger list.
- **Model-invoked**: reachable by **model or user**. The default: omit `disable-model-invocation` and the `policy` block. The `description` is **model-facing** and carries the trigger branches ("Use when…") so the agent fires it on its own. The test for keeping a skill model-invoked: _could the agent usefully reach for this without being told?_

## `agents/openai.yaml`

Every skill carries an `agents/openai.yaml` beside its `SKILL.md`, holding Codex UI metadata: `interface.display_name` and `interface.short_description` for the skill picker, plus, for a user-invoked skill, the `policy.allow_implicit_invocation: false` that pairs with `disable-model-invocation`. A skill is user-invoked in both files or in neither.

```yaml
interface:
  display_name: "Prototype Code"
  short_description: "Compare throwaway code variants side by side"
policy: # user-invoked skills only
  allow_implicit_invocation: false
```

## One skill calling another

A skill's step that runs another skill says so as an explicit instruction to **call the Skill tool** with the skill's name (`Call the Skill tool with "grilling"`). Naming the tool is what gets it fired, and the bare name carries no harness-specific `/` syntax. Shared reference lives inside the skill that owns it; other skills reach it by calling that skill, never by linking into its folder.

The Skill tool takes one skill per call, so a step that needs two skills says so: `Call the Skill tool twice, for "grilling" and "domain-modeling"`.

Only a **model-invoked** skill can be reached this way. When a step depends on a user-invoked skill, phrase it as an instruction to the human: "tell the user to run `/<name>`".
