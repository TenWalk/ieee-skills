# IEEE Skills

This repository contains two platform-adapted packages for the same IEEE communications manuscript
skills.

| Package | Path | Target |
|---|---|---|
| Codex package | [`ieee-skills-codex/`](ieee-skills-codex/) | Codex plugin or direct `~/.codex/skills` installation |
| Claude package | [`ieee-skills-claude/`](ieee-skills-claude/) | Claude Code / Cowork plugin installation |

Both packages contain the same 11 IEEE skill bodies and reference files:

- `ieee-writing`
- `ieee-polishing`
- `ieee-citation`
- `ieee-experiments`
- `ieee-figure`
- `ieee-response`
- `ieee-letter`
- `ieee-methods`
- `ieee-cover`
- `ieee-search`
- `ieee-latex`

The Codex package additionally includes per-skill `agents/openai.yaml` files and
`.codex-plugin/plugin.json`. The Claude package includes `.claude-plugin/` metadata.

## Quick Install

### Codex

Use the Codex-adapted package:

```bash
cp -R ieee-skills-codex/skills/ieee-* ~/.codex/skills/
```

Restart Codex after copying.

### Claude / Cowork

Use the Claude-adapted package:

```bash
cd ieee-skills-claude
/plugin marketplace add <path-or-git-url-to-this-folder>
/plugin install ieee-skills
/reload-plugins
```

## Package Consistency

The two package folders are intended to stay content-identical at the skill level. Platform-specific
differences are limited to metadata and UI integration files.
