# OpenAPI Template

This template represents the required baseline for API contracts in this governance demo. It is the human-readable version of the standard contract shape that the executable rules validate.

## Standard API contract template

```yaml
openapi: 3.0.3
info:
  title: API Template
  version: 1.0.0
  description: Standardized API contract template.
servers:
  - url: https://api.example.com
paths:
  /v1/users:
    get:
      summary: List users
      operationId: listUsers
      tags:
        - Users
      security:
        - bearerAuth: []
      responses:
        '200':
          description: Success
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
```

## Template requirements

The template demonstrates the required architecture baseline:

- path is versioned under `/v1`
- every operation includes an `operationId`
- every operation declares a security requirement
- standard OpenAPI metadata is present

## Governance note

This template should be used as the starting point for new APIs. If a contract does not follow this structure, it will fail the governance validation rules defined in `spectral.yaml`.
