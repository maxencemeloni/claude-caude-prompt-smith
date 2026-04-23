# Security Policy

## Supported Versions

Only the latest released version of Prompt Smith receives security updates.

| Version | Supported |
|---------|-----------|
| Latest  | ✅        |
| Older   | ❌        |

Check the current version in [`VERSION`](./VERSION) or the [Releases page](https://github.com/maxencemeloni/claude-code-prompt-smith/releases).

---

## Reporting a Vulnerability

If you discover a security vulnerability in Prompt Smith, please report it **privately** rather than opening a public issue.

### How to Report

Email **maxence@mmapi.fr** with:

- A clear description of the vulnerability
- Steps to reproduce (if applicable)
- The version affected
- Any suggested mitigation

### What to Expect

- **Acknowledgement** within 72 hours
- **Initial assessment** within 7 days
- **Fix or mitigation plan** communicated once triaged
- **Credit** in the release notes if you wish (optional)

Please do not disclose the issue publicly until a fix has been released.

---

## Scope

Prompt Smith is a slash command for Claude Code. It optimizes prompt text and then hands the result to Claude Code for execution. Relevant security concerns include:

- Prompt injection that could cause the optimizer to change a user's intent
- Command files that could be tampered with in transit (via the plugin marketplace)
- Misleading preview output that hides what will actually be executed

Out of scope:

- Vulnerabilities in Claude Code itself (report to Anthropic)
- Vulnerabilities in third-party plugins

---

## Contact

For security questions that are not vulnerability reports, open a regular issue or email **maxence@mmapi.fr**.
