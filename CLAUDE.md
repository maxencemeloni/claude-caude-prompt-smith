# Prompt Smith Development Context

This file provides context for AI assistants (Claude Code) when working on Prompt Smith itself.
It is NOT loaded when users run Prompt Smith commands in their own projects.

---

## Project Identity

Prompt Smith is a slash command for Claude Code that optimizes rough prompts into cleaner, more executable versions. The core principle is **fidelity first** — the optimized prompt must preserve the user's exact intent while improving clarity, structure, and actionability.

---

## Understanding Suggestions

When the user proposes an idea or improvement, **always clarify the intent first** before responding:

- **"For the users"** — The suggestion is about what Prompt Smith should **do for people who run the command**. This means improving the optimization logic, adding modes, or changing how the preview/confirmation works.
- **"For the tool"** — The suggestion is about improving Prompt Smith's **internal structure**, commands, or architecture. This is contributor/maintainer work.

**Do not assume.** If the intent is ambiguous, ask: *"Is this something Prompt Smith should do when optimizing prompts, or a change to how Prompt Smith itself works?"*

---

## Design Principles

1. **Fidelity first** — Never silently change the user's intended outcome
2. **Claude Code native** — Optimized prompts should be terminal-ready instructions, not generic chat
3. **Minimal structure** — Add structure only when it improves execution quality
4. **Confirmation by default** — Never execute without explicit user consent (unless `--yes`)
5. **Developer respect** — No dumbed-down language; users are professionals

---

## Optimization Modes

| Mode | Purpose | When to Use |
|------|---------|-------------|
| `default` | General cleanup | Most prompts |
| `agentic` | Execution-focused structure | Orchestration, automation, multi-step delivery |
| `compact` | Shortest clean version | Utility prompts, brevity wanted |
| `strict` | Maximum fidelity | Sensitive wording, policy text |

---

## What's Explicitly Out of Scope

Prompt Smith is not:

| Out of Scope | Why |
|--------------|-----|
| Code analysis tool | It optimizes prompts, not code |
| Repo refactoring tool | It rewrites prompts, not files |
| Task-specific plugin | It's a prompt optimizer and launcher |
| Autonomous executor | It requires confirmation before action |

---

## Commands Overview

| Command | Purpose |
|---------|---------|
| `/prompt-smith` | Optimize a rough prompt with mode selection, preview, and confirmation |

### `/prompt-smith` Workflow

1. Parse flags and raw prompt from `$ARGUMENTS`
2. Select or infer optimization mode
3. Show preview (mode, rationale, original, optimized)
4. Wait for confirmation (execute / regenerate / cancel)
5. Execute the optimized prompt if confirmed

---

## Version Management

### Versioning Strategy

- **Patch (x.x.1)** — Wording improvements, documentation fixes, non-breaking prompt tuning
- **Minor (x.1.0)** — New flags, new modes, improved interaction patterns, non-breaking behavior changes
- **Major (2.0.0)** — Breaking command syntax, renamed modes, incompatible execution behavior, major UX changes

### When Releasing a New Version

1. **Update version badge** in `README.md`
2. **Add changelog entry** in `CHANGELOG.md` (at the top, before previous versions)
3. **Commit** with message format: `Release vX.Y.Z — Short Description`
4. **Push** to main

### Files to Update

| File | What to Update |
|------|----------------|
| `VERSION` | Replace contents with new version |
| `.claude-plugin/plugin.json` | Update `"version"` field |
| `.claude-plugin/marketplace.json` | Update `"version"` in plugins array |
| `README.md` | Version badge |
| `CHANGELOG.md` | Add new version section at top |

### Post-Release Verification

After pushing, verify the plugin update works (marketplace refresh is required before update):
```bash
claude plugin marketplace update prompt-smith-marketplace
claude plugin update prompt-smith@prompt-smith-marketplace
```
The version should match the just-released version. If not, check that both `plugin.json` and `marketplace.json` have the correct version.

---

## Repository Structure

```
claude-caude-prompt-smith/
├── .claude-plugin/
│   ├── marketplace.json    # Marketplace manifest (version + metadata)
│   └── plugin.json         # Plugin manifest
├── .claude/
│   ├── commands/           # Dev-time slash commands (local development)
│   │   ├── prompt-smith.md
│   │   └── release.md
│   └── settings.json       # Project permissions (deny rules)
├── commands/               # Plugin commands (distributed to users)
│   └── prompt-smith.md
├── assets/                 # Banner and logo images
├── CLAUDE.md               # This file (development context)
├── CHANGELOG.md            # Changelog
├── PROMPT_SMITH.md         # Core identity document (loaded by commands)
├── README.md               # User-facing documentation
└── VERSION                 # Current version
```

---

## Common Development Tasks

### Adding a New Mode

1. Add mode definition in `PROMPT_SMITH.md`
2. Add mode behavior in both `.claude/commands/prompt-smith.md` (dev) and `commands/prompt-smith.md` (plugin)
3. Update `README.md` modes table
4. Bump minor version

### Modifying Mode Behavior

1. Update `PROMPT_SMITH.md` mode definition
2. Update both command files (`.claude/commands/` and `commands/`)
3. Bump patch version

### Adding a New Flag

1. Add flag parsing in both command files
2. Update `PROMPT_SMITH.md` supported flags section
3. Update `README.md` command syntax
4. Bump minor version

### Adding a New Command

1. Create command in both `.claude/commands/` (dev) and `commands/` (plugin)
2. Update `README.md` commands section
3. Update this file's Commands Overview table
4. Bump minor version

---

## Testing

Before releasing:

1. Run `claude plugin validate .` to validate the plugin
2. Test `/prompt-smith` with a sample prompt in each mode
3. Verify the preview format renders correctly
4. Test `--yes` bypass
5. Test `--list-modes` output
6. Test empty input (usage display)

---

## Links

- **Repository:** https://github.com/maxencemeloni/claude-caude-prompt-smith
- **AI Tools Hub:** https://hub.mmapi.fr/tools?origin=claudecode
