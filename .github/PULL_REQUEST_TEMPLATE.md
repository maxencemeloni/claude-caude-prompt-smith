## Summary

What does this PR do? Keep it to 1-3 bullet points.

-
-

## Type of change

- [ ] Bug fix
- [ ] New feature (new mode, flag, or command)
- [ ] Behavior change to an existing mode
- [ ] Documentation
- [ ] Refactor (no user-facing change)

## Related issues

Closes #

## Fidelity check

Prompt Smith's core rule: **never silently change the user's intended outcome**.

- [ ] This change preserves user intent in all supported modes
- [ ] I tested the prompts listed in `CLAUDE.md` → *Test Prompts*

## Command file sync

If you modified `.claude/commands/prompt.md` or `commands/prompt.md`:

- [ ] Both files are in sync (only the `PROMPT_SMITH.md` path differs)
- [ ] I ran `diff .claude/commands/prompt.md commands/prompt.md` and confirmed

## Versioning

- [ ] No version bump needed
- [ ] Patch (wording / docs / non-breaking tuning)
- [ ] Minor (new flag, new mode, non-breaking behavior change)
- [ ] Major (breaking syntax or behavior)

## Changelog

- [ ] Updated `CHANGELOG.md` (or this change is not user-facing)

## Checklist

- [ ] I have read [`CONTRIBUTING.md`](../CONTRIBUTING.md)
- [ ] My changes follow the project's design principles in `CLAUDE.md`
- [ ] I tested the change locally
