# API Governance Demo

This repo is a simple proof that architecture standards can be converted into executable governance controls.

## What this demo proves

- A written standard can be translated into machine-enforceable rules.
- A compliant API passes validation.
- A noncompliant API fails validation.
- GitHub Actions can enforce the standard automatically in pull requests and pushes.

## Repository layout

- `standards/API-Design-Standards.md` — human-readable architecture standard.
- `standards/spectral.yaml` — executable governance rules.
- `templates/openapi-template.md` — readable version of the required API contract shape.
- `templates/openapi-template.yaml` — example OpenAPI baseline.
- `examples/compliant-api.yaml` — valid example that passes.
- `examples/noncompliant-api.yaml` — invalid example that fails.
- `.github/workflows/api-validation.yml` — CI enforcement.

## Demo flow

1. A written architecture policy is captured in Markdown.
2. That policy is translated into Spectral rules.
3. A compliant contract is validated successfully.
4. A noncompliant contract fails with specific governance errors.
5. GitHub Actions runs the same checks automatically in PRs and on pushes.

## Local validation

From the repo root, run:

```bash
cd api-governance-demo
npx @stoplight/spectral-cli lint examples/compliant-api.yaml -r standards/spectral.yaml
npx @stoplight/spectral-cli lint examples/noncompliant-api.yaml -r standards/spectral.yaml
```

Expected result:

- the compliant API passes
- the noncompliant API fails with errors such as missing `/v1` path versioning, missing `operationId`, or missing security

## Governance interpretation

This is the core idea behind the demo:

- the standard explains the requirement
- the rule file converts that requirement into code
- CI enforces the rule automatically

That turns policy from a document into a control.
