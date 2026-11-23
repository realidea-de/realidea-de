# Agent guide — realidea-de

This repository is **GSD-managed IaC**: Cursor agent prompts, rules, and GitHub
workflows. There is no application runtime here—dependency and deploy security
belongs in the application repository that holds production code.

## Where to read instructions

| Topic | File |
|-------|------|
| Role definitions (Coding, QA, Security, DevOps, …) | [`.cursor/rules/agent-roles.md`](.cursor/rules/agent-roles.md) |
| Security expectations | [`.cursor/rules/security-standards.md`](.cursor/rules/security-standards.md) |
| Coding style | [`.cursor/rules/coding-standards.md`](.cursor/rules/coding-standards.md) |
| Testing | [`.cursor/rules/testing-standards.md`](.cursor/rules/testing-standards.md) |
| Per-agent system prompts | [`.cursor/agent-prompts/`](.cursor/agent-prompts/) |

## Every agent run

1. Identify your role from the task title or workflow prompt.
2. Read the matching row in the table above before changing anything.
3. Keep changes minimal and aligned with existing workflow patterns in
   `.github/workflows/`.

## Security agent (weekly cron)

- `pnpm audit` applies only when `pnpm-lock.yaml` exists; otherwise skip with
  notice.
- `SNYK_TOKEN` must be set in GitHub Actions secrets for Snyk scans.
- `gitleaks` is enforced via [`.github/workflows/security.yml`](.github/workflows/security.yml).