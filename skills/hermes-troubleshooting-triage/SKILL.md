---
name: hermes-troubleshooting-triage
description: Diagnose Hermes Agent setup/config/profile/provider/tool/gateway failures from redacted symptoms and logs.
version: 1.0.0
author: Volcanic
license: MIT
---

# Hermes Troubleshooting Triage

## When to Use

Use when a user reports Hermes install, profile, config, model/provider, toolset, MCP, cron, gateway, or runtime failures.

## Workflow

1. State the symptom in one sentence.
2. Identify the subsystem: install, config, provider/model, toolsets, profile distribution, MCP, cron, gateway, terminal/filesystem, or external service.
3. Ask only for safe minimal diagnostics if needed:
   - exact error text
   - `hermes doctor` output
   - redacted `config.yaml` section
   - redacted `.env.EXAMPLE`-style variable names
   - relevant log tail with tokens removed
4. Build a hypothesis list ranked by evidence.
5. Give fix steps with verification commands.
6. If unresolved, produce a redacted issue report.

## Output Template

- Symptom:
- Subsystem:
- Evidence:
- Most likely cause:
- Fix steps:
- Verify with:
- If still broken:

## Safety Rules

- Never request secrets, raw `auth.json`, cookies, wallet files, private keys, or full unredacted `.env`.
- Do not recommend deleting profiles/configs until backup or non-destructive checks are tried.
- Mark destructive commands clearly.
