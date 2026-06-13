---
name: redacted-issue-report
description: Convert Hermes errors/logs/config snippets into safe public issue reports without secrets or private state.
version: 1.0.0
author: Volcanic
license: MIT
---

# Redacted Issue Report

## Workflow

1. Extract the failure summary.
2. Redact secrets and personal data:
   - API keys/tokens/passwords
   - emails/phone numbers if not needed
   - wallet/private key material
   - cookies/session IDs
   - private repo URLs if requested
3. Preserve useful technical context:
   - OS/platform
   - Hermes version
   - command run
   - profile name/repo if public
   - provider/model names
   - exact non-secret error text
4. Produce a minimal reproducible issue.

## Template

```markdown
## Summary

## Environment
- OS:
- Hermes version:
- Install method:
- Profile/provider/toolset involved:

## Command / action

## Expected behavior

## Actual behavior

## Relevant redacted logs

## What I already tried
```

## Pitfalls

- Do not over-redact error types, stack frames, file names, or version numbers; those are usually useful.
- Do redact credentials and local secrets even if the user forgot.
