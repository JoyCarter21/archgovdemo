# API Governance Demo

This demo shows how architecture standards can be expressed as executable governance controls.

## What this proves

- A written standard is mapped into a machine-enforceable rule set.
- A compliant API passes validation.
- A noncompliant API fails validation.
- GitHub Actions can enforce the standard automatically for pull requests and pushes.

## Files

- `standards/API-Design-Standards.docx` — human-readable architecture standard.
- `standards/spectral.yaml` — executable governance rules.
- `templates/openapi-template.yaml` — a standard API template.
- `examples/compliant-api.yaml` — valid example that passes.
- `examples/noncompliant-api.yaml` — invalid example that fails.
- `.github/workflows/api-validation.yml` — CI enforcement.

## Local validation

```bash
cd api-governance-demo
npx @stoplight/spectral-cli lint examples/compliant-api.yaml -r standards/spectral.yaml
npx @stoplight/spectral-cli lint examples/noncompliant-api.yaml -r standards/spectral.yaml
```

The first command should pass, and the second should fail.
