# human-handoff-skill

A minimal agent skill for human-in-the-loop pauses.

Use it when an agent is blocked, needs manual help, faces risky side effects, or is about to waste tokens on repeated speculative attempts.

## Install in Pi

```bash
pi install https://github.com/xz-dev/human-handoff-skill
```

Pi auto-discovers the top-level `skills/` directory and loads `skills/human-handoff/SKILL.md`, so no manual symlink or `package.json` is needed.

## Install in Hermes

```bash
hermes skills install xz-dev/human-handoff-skill/skills/human-handoff --category software-development --yes
```

## Update

```bash
hermes skills check human-handoff
hermes skills update human-handoff
```

The installable skill lives in `skills/human-handoff/SKILL.md`.
