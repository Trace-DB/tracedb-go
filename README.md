# TraceDB Go SDK

This repository is reserved for the future official Go SDK.

No Go SDK implementation, module path, package artifact, or verification smoke is
present yet. When implementation starts, it should follow the same contract
boundaries as the Rust, TypeScript, and Python SDKs and should not claim release
readiness until the smoke path below exists.

## Planned Scope

- `Client` constructed from explicit config or `FromEnv()`.
- `Table` handle for tenant-scoped record operations.
- Safe retries for read-only routes only.
- Idempotency retries for keyed mutation/admin routes only.
- Typed error surface with method, path, status, raw body, parsed error, and
  optional code.
- `User-Agent: tracedb-go/<version>` on requests.
- Protocol lock pinned to `tracedb-protocol` once code exists.

## Initial Package Shape

```text
tracedb-go/
  go.mod
  client.go
  errors.go
  models.go
  retry.go
  client_test.go
```

## First PR Checklist

Before this repository claims an implemented SDK, add:

- A `tracedb-protocol.lock` pinned to the current protocol revision.
- Minimal typed request/response models for the v0 HTTP routes used by the
  smoke test.
- A sync `Client` with explicit config and `FromEnv()` construction.
- Table handles for schema apply, insert, scan/get/delete, and hybrid query.
- Tests for request shape, auth headers, retry boundaries, and error parsing.
- A local HTTP smoke that starts or targets a TraceDB server and exits non-zero
  on failure.
- README commands that a new contributor can run from a fresh checkout.

The first implementation should target `platform-contract-v0` and include a
local HTTP smoke comparable to the existing Python and TypeScript SDK smokes.
