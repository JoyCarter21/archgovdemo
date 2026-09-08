# API Design Standards

This document defines the baseline architecture standards for all APIs in this demo. These standards are intentionally simple and are converted into machine-enforceable governance controls through Spectral rules.

## Standards

1. All API paths must be versioned under `/v1`.
2. Every API operation must define an `operationId`.
3. Every API operation must declare a security requirement.
4. APIs should use a consistent naming pattern and standard OpenAPI structure.
5. The API contract should be reviewed and validated before release.

## Why these standards matter

These standards help ensure:

- predictable API evolution
- clear ownership and operability
- security-by-default design
- easier governance and review
- consistent contract quality across teams

## Governance mapping

These architectural standards are enforced by the executable rule file in this folder:

- `spectral.yaml`

The rule file translates the written standard into automated checks that fail when an API contract violates the standard.

## Example governance interpretation

- A path like `/users` is noncompliant because it is not versioned.
- A route without `operationId` is noncompliant because it weakens traceability and tooling.
- A route without `security` is noncompliant because it does not enforce access controls.

## Summary

The purpose of this standard is not only to document policy, but to make it executable in CI and pull requests. Once captured as rules, the standard becomes a governance control rather than a recommendation.
