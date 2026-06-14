# Reference
## admin
<details><summary><code>client.Tracedb.Admin.PostAdminCompact(request) -> *tracedb.CompactResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
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
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**request:** `tracedb.EmptyObject` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Admin.GetAdminJobs() -> *tracedb.JobsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.GetAdminJobsRequest{}
client.Tracedb.Admin.GetAdminJobs(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**databaseID:** `*string` — Canonical managed-routing database identifier for bodyless routes. SDKs must use this parameter name (not db_id, databaseId, or similar variants) so all SDKs target the same gateway routing key.
    
</dd>
</dl>

<dl>
<dd>

**branchID:** `*string` — Canonical managed-routing branch identifier for bodyless routes. SDKs must use this parameter name (not br_id, branchId, or similar variants) so all SDKs target the same gateway routing key.
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Admin.PostAdminRestore(request) -> *tracedb.RestoreResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RestoreRequest{}
client.Tracedb.Admin.PostAdminRestore(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**source:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**target:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**verifyRecord:** `*tracedb.RecordGetRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Admin.PostAdminSnapshot(request) -> *tracedb.SnapshotResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.SnapshotRequest{}
client.Tracedb.Admin.PostAdminSnapshot(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**target:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## catalog
<details><summary><code>client.Tracedb.Catalog.GetBranches() -> *tracedb.BranchesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Catalog.GetBranches(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Catalog.GetDatabases() -> *tracedb.DatabasesResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Catalog.GetDatabases(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## query
<details><summary><code>client.Tracedb.Query.PostExplain(request) -> *tracedb.HybridExplain</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.HybridQuery{}
client.Tracedb.Query.PostExplain(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*tracedb.HybridQuery` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Query.PostGraphql(request) -> *tracedb.GraphQlResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.PostGraphqlRequest{
        Body: &tracedb.GraphQlQueryRequest{},
    }
client.Tracedb.Query.PostGraphql(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*tracedb.GraphQlQueryRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Query.PostGraphqlBounded(request) -> *tracedb.QueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.GraphQlQueryRequest{}
client.Tracedb.Query.PostGraphqlBounded(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*tracedb.GraphQlQueryRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Query.GetGraphqlSchema() -> *tracedb.GraphQlSchemaResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Query.GetGraphqlSchema(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Query.PostQuery(request) -> *tracedb.QueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.HybridQuery{}
client.Tracedb.Query.PostQuery(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*tracedb.HybridQuery` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Query.PostTraceql(request) -> *tracedb.QueryResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.TraceQlQueryRequest{}
client.Tracedb.Query.PostTraceql(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**query:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## health
<details><summary><code>client.Tracedb.Health.GetHealth() -> *tracedb.HealthResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Health.GetHealth(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## records
<details><summary><code>client.Tracedb.Records.PostInsert(request) -> *tracedb.EpochResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Deprecated. Use POST /v1/records/put instead. This route remains for backwards compatibility and will be removed in a future release.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.PostInsertRequest{
        Body: &tracedb.RecordInput{},
    }
client.Tracedb.Records.PostInsert(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*tracedb.RecordInput` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsDelete(request) -> *tracedb.DeleteResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RecordDeleteRequest{}
client.Tracedb.Records.PostRecordsDelete(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**id:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**table:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**tenantID:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**tombstone:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsGet(request) -> *tracedb.GetRecordResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RecordGetRequest{}
client.Tracedb.Records.PostRecordsGet(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**request:** `*tracedb.RecordGetRequest` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsPatch(request) -> *tracedb.EpochResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RecordPatchRequest{}
client.Tracedb.Records.PostRecordsPatch(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**fields:** `map[string]any` — Patch field map.
    
</dd>
</dl>

<dl>
<dd>

**id:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**table:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**tenantID:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsPut(request) -> *tracedb.EpochResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.PostRecordsPutRequest{
        Body: &tracedb.RecordPutBody{
            RecordInput: &tracedb.RecordInput{},
        },
    }
client.Tracedb.Records.PostRecordsPut(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**request:** `*tracedb.RecordPutBody` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsPutBatch(request) -> *tracedb.PutBatchResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RecordPutBatchRequest{}
client.Tracedb.Records.PostRecordsPutBatch(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**includeWriteTiming:** `*bool` 
    
</dd>
</dl>

<dl>
<dd>

**records:** `[]*tracedb.RecordInput` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

<details><summary><code>client.Tracedb.Records.PostRecordsScan(request) -> *tracedb.RecordScanOutput</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.RecordScanRequest{}
client.Tracedb.Records.PostRecordsScan(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**cursor:** `*string` — Opaque cursor returned by the previous scan page.
    
</dd>
</dl>

<dl>
<dd>

**limit:** `*int` 
    
</dd>
</dl>

<dl>
<dd>

**table:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**tenantID:** `*string` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## metrics
<details><summary><code>client.Tracedb.Metrics.GetMetricsPublicSafe() -> *tracedb.MetricsResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Metrics.GetMetricsPublicSafe(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## readiness
<details><summary><code>client.Tracedb.Readiness.GetReady() -> *tracedb.ReadyResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
client.Tracedb.Readiness.GetReady(
        context.TODO(),
    )
}
```
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

## schema
<details><summary><code>client.Tracedb.Schema.PostSchemaApply(request) -> *tracedb.EpochResponse</code></summary>
<dl>
<dd>

#### 📝 Description

<dl>
<dd>

<dl>
<dd>

Current TraceDB v1 product route. This OpenAPI artifact is generated from the checked-in route manifest.
</dd>
</dl>
</dd>
</dl>

#### 🔌 Usage

<dl>
<dd>

<dl>
<dd>

```go
request := &tracedb.TableSchema{}
client.Tracedb.Schema.PostSchemaApply(
        context.TODO(),
        request,
    )
}
```
</dd>
</dl>
</dd>
</dl>

#### ⚙️ Parameters

<dl>
<dd>

<dl>
<dd>

**idempotencyKey:** `*string` — Optional local data-dir replay key scoped by method and path. Receipts are WAL/checkpoint-backed in the local engine. same key plus same raw request body replays the first successful response; same key with a different body returns 409 Conflict.
    
</dd>
</dl>

<dl>
<dd>

**name:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**primaryIDColumn:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**scalarColumns:** `[]string` 
    
</dd>
</dl>

<dl>
<dd>

**tenantIDColumn:** `*string` 
    
</dd>
</dl>

<dl>
<dd>

**textIndexedColumns:** `[]string` 
    
</dd>
</dl>

<dl>
<dd>

**vectorColumns:** `[]map[string]any` 
    
</dd>
</dl>
</dd>
</dl>


</dd>
</dl>
</details>

