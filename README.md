# volcanic-hermes-doctor

Public-safe Hermes troubleshooting profile for diagnosing install, config, provider, toolset, profile, and runtime issues from redacted logs.

## Install

```bash
hermes profile install github.com/VolcanicWorks/volcanic-hermes-doctor --name volcanic-hermes-doctor
```

## Run

```bash
hermes -p volcanic-hermes-doctor chat
```

## Update

```bash
hermes profile update volcanic-hermes-doctor
```

One-shot example:

```bash
hermes -p volcanic-hermes-doctor chat -q "Hermes profile install failed with this error: <redacted error>. Diagnose likely causes and give verification steps."
```

## Expected output shape

A good diagnosis should look like:

- Symptom: the visible failure in one sentence.
- Subsystem: install, config, provider/model, toolsets, gateway, MCP, cron, or external service.
- Evidence: exact non-secret clues from the error/logs.
- Most likely cause: ranked, not guessed as fact.
- Fix steps: smallest safe commands first.
- Verify with: command or behavior that proves the fix worked.
- If still broken: a redacted issue report using `templates/redacted_issue_report.md`.

## Example tasks

- "Hermes says my model provider is missing — diagnose this from my config snippet."
- "My profile install failed. Here is the error; tell me what to check next."
- "Telegram gateway stopped responding. Help me inspect logs safely."
- "Turn this failing Hermes setup into a clean GitHub issue report with secrets redacted."

## Toolset rationale

This profile requests web access for public docs/issues, terminal/file/code execution for local diagnostics and log parsing, and skills for its bundled troubleshooting workflows. It does not request `all`, wallet, admin, messaging, or cron toolsets by default. It should not perform destructive changes unless the user explicitly asks and understands the command.

## Privacy note

Do not paste API keys, passwords, auth tokens, private keys, cookies, wallet files, or full unredacted `.env` content. Use placeholders like `OPENROUTER_API_KEY is set but redacted`.


## Requirements

- Hermes Agent >= 0.15.0.
- Python 3 for the optional local secret/private-state scanner.
- If you do not have access to the default model in `config.yaml`, override with `--model` or edit the profile config after install.

## What is included

- `SOUL.md` — profile persona and operating principles.
- `config.yaml` — conservative non-secret Hermes defaults.
- `distribution.yaml` — installable profile distribution metadata.
- `profile.yaml` — short registry-facing profile metadata.
- `.env.EXAMPLE` — empty placeholder file; no secrets.
- `skills/` — bundled reusable workflows for this profile.
- `templates/redacted_issue_report.md` — reusable safe issue-report template.
- `scripts/profile_secret_scan.py` — local scanner for common secrets/private state.
- `cron/README.md` — explicit note that no cron jobs are enabled by default.

## Validate before publishing

```bash
python3 scripts/profile_secret_scan.py .
hermes profile install github.com/VolcanicWorks/volcanic-hermes-doctor --name volcanic-hermes-doctor-smoke -y
hermes profile show volcanic-hermes-doctor-smoke
hermes profile delete volcanic-hermes-doctor-smoke -y
```

## Branding/provenance

Published under the `VolcanicWorks` GitHub account with `Volcanic` as the profile author/brand. This is a public-service profile, not a private Volcanic operating profile.

## License

MIT
