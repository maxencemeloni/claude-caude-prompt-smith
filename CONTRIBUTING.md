# Contributing to Prompt Smith

Thanks for your interest in contributing to Prompt Smith! This document explains how to propose changes, report issues, and submit pull requests.

---

## Core Principle: Fidelity First

Prompt Smith optimizes rough prompts into cleaner, more executable versions. The core rule is: **the optimized prompt must preserve the user's exact intent**. Any contribution that risks silently changing a user's intended outcome will not be accepted.

Before proposing a change, read [`PROMPT_SMITH.md`](./PROMPT_SMITH.md) and [`CLAUDE.md`](./CLAUDE.md) to understand the project's identity and design principles.

---

## Ways to Contribute

- **Report a bug** — open an issue with a clear reproduction case
- **Request a feature** — open an issue describing the problem you're trying to solve
- **Improve the docs** — fix typos, clarify wording, add examples
- **Tune the optimization logic** — refine how modes work or add new modes
- **Submit a pull request** — see the PR workflow below

---

## Before You Start

1. **Check existing issues** — someone may already be working on the same thing
2. **Open an issue first** for non-trivial changes — align on the approach before writing code
3. **Keep changes focused** — one PR per logical change

---

## Development Setup

Prompt Smith is a Claude Code slash command plugin. No build step is required.

```
claude-code-prompt-smith/
├── .claude/commands/        # Dev-time commands (local testing)
├── commands/                # Plugin commands (distributed to users)
├── PROMPT_SMITH.md          # Core identity
├── CLAUDE.md                # Development context
└── README.md                # User docs
```

After modifying a command file, **keep `.claude/commands/prompt.md` and `commands/prompt.md` in sync**. The only difference should be the `PROMPT_SMITH.md` path.

Verify with:

```bash
diff .claude/commands/prompt.md commands/prompt.md
```

---

## Testing Your Changes

Use these prompts to verify each mode still behaves correctly:

| Prompt | Expected Mode |
|--------|---------------|
| `fix the bug` | default |
| `orchestrate the deploy pipeline with validation at each step` | agentic |
| `rename x to y` | compact |
| `Update the privacy policy section 3.2 to reflect the new data retention period` | strict |
| `--help` | shows usage |
| `(empty)` | shows usage |

---

## Pull Request Workflow

1. Fork the repository
2. Create a branch from `main`: `git checkout -b my-feature`
3. Make your changes (keep commits focused)
4. Test locally using the matrix above
5. Update `CHANGELOG.md` under an "Unreleased" section if your change affects users
6. Open a PR against `main` with a clear description of **what** changed and **why**

---

## Commit Style

- Use imperative mood in the first line (e.g., "Add strict mode", not "Added strict mode")
- Keep the first line under ~70 characters
- Add a body if the change needs explanation

---

## Code of Conduct

This project follows a [Code of Conduct](./CODE_OF_CONDUCT.md). By participating, you agree to uphold it.

---

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](./LICENSE).

---

## Questions?

Open a [GitHub issue](https://github.com/maxencemeloni/claude-code-prompt-smith/issues) or reach out at **maxence@mmapi.fr**.
