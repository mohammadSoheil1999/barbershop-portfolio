# Architecture

## Component boundaries

The React client owns presentation and interaction. The Express API authenticates requests, applies role and tenant guards, validates commands, and delegates to appointment, user, settings, and notification services. MariaDB is the operational data store.

## Tenant boundary

```mermaid
sequenceDiagram
  actor User
  participant Client
  participant API
  participant Auth
  participant DB as MariaDB
  User->>Client: Sign in for selected business
  Client->>API: Credentials and tenant entry context
  API->>DB: Resolve tenant and account
  API->>Auth: Issue signed token with tenant and role
  Auth-->>Client: Authenticated session token
  Client->>API: Protected appointment request
  API->>Auth: Verify signature, tenant, role
  Auth->>DB: Tenant-scoped query or transaction
  DB-->>Client: Authorized result
```

Browser-supplied tenant selection helps find the correct public entry point, but it does not authorize protected data access. Protected queries use verified authentication state.

## Data model overview

Tenants own customers, appointments, and visual settings. Customer identity and appointment-slot uniqueness are scoped within a tenant. This preserves a reusable shared runtime without allowing one business to address another business's records.

