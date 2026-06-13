# TraceDb Go Library

[![fern shield](https://img.shields.io/badge/%F0%9F%8C%BF-Built%20with%20Fern-brightgreen)](https://buildwithfern.com?utm_source=github&utm_medium=github&utm_campaign=readme&utm_source=https%3A%2F%2Fgithub.com%2FTrace-DB%2Ftracedb-go)

The TraceDb Go library provides convenient access to the TraceDb APIs from Go.

## Table of Contents

- [Split Checkpoint](#split-checkpoint)
- [Registry Status](#registry-status)
- [Planned Scope](#planned-scope)
- [Initial Package Shape](#initial-package-shape)
- [First Pr Checklist](#first-pr-checklist)
- [Reference](#reference)
- [Usage](#usage)
- [Environments](#environments)
- [Errors](#errors)
- [Request Options](#request-options)
- [Advanced](#advanced)
  - [Response Headers](#response-headers)
  - [Retries](#retries)
  - [Timeouts](#timeouts)
  - [Explicit Null](#explicit-null)
- [Contributing](#contributing)

## Split Checkpoint

Status: **future-only** after the Trace-DB organization split.

Checkpoint plan:

1. Keep this repository as a documented placeholder until Go SDK work is
   explicitly prioritized.
2. Do not add package metadata, release automation, or SDK claims before the
   first implementation PR.
3. Start implementation only after pinning a `tracedb-protocol.lock` and
   defining the initial smoke path.

This repository is reserved for the future official Go SDK.

No Go SDK implementation, module path, package artifact, or verification smoke is
present yet. When implementation starts, it should follow the same contract
boundaries as the Rust, TypeScript, and Python SDKs and should not claim release
readiness until the smoke path below exists.

This repository is public as a language-SDK placeholder only. It does not
contain hosted TraceDB SaaS internals, operator tooling, or deployment
automation.

## Registry Status

No Go SDK implementation, Go module path, or package artifact is published for
TraceDB yet. The public Go module proxy has no versioned `tracedb-go` releases
for this organization lane. Any Go package or module claim should remain
planned-only until the first implementation PR defines the module path,
protocol lock, and smoke path.

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

## Reference

A full reference for this library is available [here](https://github.com/Trace-DB/tracedb-go/blob/HEAD/./reference.md).

## Usage

Instantiate and use the client with the following:

```go
package example

import (
    context "context"

    client "github.com/Trace-DB/tracedb-go/client"
    option "github.com/Trace-DB/tracedb-go/option"
    tracedb "github.com/Trace-DB/tracedb-go/tracedb"
)

func do() {
    client := client.NewClient(
        option.WithToken(
            "<token>",
        ),
    )
    request := &tracedb.PostAdminCompactRequest{
        Body: map[string]any{
            "key": "value",
        },
    }
    client.Tracedb.Admin.PostAdminCompact(
        context.TODO(),
        request,
    )
}
```

## Environments

You can choose between different environments by using the `option.WithBaseURL` option. You can configure any arbitrary base
URL, which is particularly useful in test environments.

```go
client := client.NewClient(
    option.WithBaseURL(api.Environments.Default),
)
```

## Errors

Structured error types are returned from API calls that return non-success status codes. These errors are compatible
with the `errors.Is` and `errors.As` APIs, so you can access the error like so:

```go
response, err := client.Tracedb.Admin.PostAdminCompact(...)
if err != nil {
    var apiError *core.APIError
    if errors.As(err, apiError) {
        // Do something with the API error ...
    }
    return err
}
```

## Request Options

A variety of request options are included to adapt the behavior of the library, which includes configuring
authorization tokens, or providing your own instrumented `*http.Client`.

These request options can either be
specified on the client so that they're applied on every request, or for an individual request, like so:

> Providing your own `*http.Client` is recommended. Otherwise, the `http.DefaultClient` will be used,
> and your client will wait indefinitely for a response (unless the per-request, context-based timeout
> is used).

```go
// Specify default options applied on every request.
client := client.NewClient(
    option.WithToken("<YOUR_API_KEY>"),
    option.WithHTTPClient(
        &http.Client{
            Timeout: 5 * time.Second,
        },
    ),
)

// Specify options for an individual request.
response, err := client.Tracedb.Admin.PostAdminCompact(
    ...,
    option.WithToken("<YOUR_API_KEY>"),
)
```

## Advanced

### Response Headers

You can access the raw HTTP response data by using the `WithRawResponse` field on the client. This is useful
when you need to examine the response headers received from the API call. (When the endpoint is paginated,
the raw HTTP response data will be included automatically in the Page response object.)

```go
response, err := client.Tracedb.Admin.WithRawResponse.PostAdminCompact(...)
if err != nil {
    return err
}
fmt.Printf("Got response headers: %v", response.Header)
fmt.Printf("Got status code: %d", response.StatusCode)
```

### Retries

The SDK is instrumented with automatic retries with exponential backoff. A request will be retried as long
as the request is deemed retryable and the number of retry attempts has not grown larger than the configured
retry limit (default: 2).

Which status codes are retried depends on the `retryStatusCodes` generator configuration:

**`legacy`** (current default): retries on
- [408](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/408) (Timeout)
- [429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) (Too Many Requests)
- [5XX](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses) (All server errors, including 500)

**`recommended`**: retries on
- [408](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/408) (Timeout)
- [429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/429) (Too Many Requests)
- [502](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/502) (Bad Gateway)
- [503](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/503) (Service Unavailable)
- [504](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/504) (Gateway Timeout)

If the `Retry-After` header is present in the response, the SDK will prioritize respecting its value exactly
over the default exponential backoff.

Use the `option.WithMaxAttempts` option to configure this behavior for the entire client or an individual request:

```go
client := client.NewClient(
    option.WithMaxAttempts(1),
)

response, err := client.Tracedb.Admin.PostAdminCompact(
    ...,
    option.WithMaxAttempts(1),
)
```

### Timeouts

Setting a timeout for each individual request is as simple as using the standard context library. Setting a one second timeout for an individual API call looks like the following:

```go
ctx, cancel := context.WithTimeout(ctx, time.Second)
defer cancel()

response, err := client.Tracedb.Admin.PostAdminCompact(ctx, ...)
```

### Explicit Null

If you want to send the explicit `null` JSON value through an optional parameter, you can use the setters\
that come with every object. Calling a setter method for a property will flip a bit in the `explicitFields`
bitfield for that setter's object; during serialization, any property with a flipped bit will have its
omittable status stripped, so zero or `nil` values will be sent explicitly rather than omitted altogether:

```go
type ExampleRequest struct {
    // An optional string parameter.
    Name *string `json:"name,omitempty" url:"-"`

    // Private bitmask of fields set to an explicit value and therefore not to be omitted
    explicitFields *big.Int `json:"-" url:"-"`
}

request := &ExampleRequest{}
request.SetName(nil)

response, err := client.Tracedb.Admin.PostAdminCompact(ctx, request, ...)
```

## Contributing

While we value open-source contributions to this SDK, this library is generated programmatically.
Additions made directly to this library would have to be moved over to our generation code,
otherwise they would be overwritten upon the next generated release. Feel free to open a PR as
a proof of concept, but know that we will not be able to merge it as-is. We suggest opening
an issue first to discuss with us!

On the other hand, contributions to the README are always very welcome!
