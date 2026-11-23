# CodeJackRabbit JavaScript API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImIwNjc4MWEyNmM0NDY5ZThmMTI4MzBhMDRkNDU1OTU3YmY2MjBkNDJiOWUxZGYxNTVlOTNlZTAwZjI5M2QxYzkiLCJvcGVyYXRpb25fY291bnQiOjI4LCJyZW5kZXJlciI6ImphdmFzY3JpcHQiLCJ2ZXJzaW9uIjoiMS41LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `b06781a26c4469e8f12830a04d455957bf620d42b9e1df155e93ee00f293d1c9`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **verified**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new Client({ hooks })` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. `beforeRequest` is the one hook that may change the request (the documented per-request credential contract, which also reads credentials masked); the other three receive frozen `HookContext` copies.

`new Client({ tracer })` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `AuditContextRequest`
- `AuditSnapshotsRequest`
- `ComplianceGateRequest`
- `DeveloperAuditRequest`
- `DeveloperEvidenceRequest`
- `FileChange`
- `FinOpsRequest`
- `ManagedDeveloperIdentity`
- `ManagedDeveloperIdentityRequest`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplQ29udHJhY3REcmlmdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCIsInBhdGgiOiIvdjEvYW5hbHlzaXMvY29udHJhY3QtZHJpZnQiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiJkMDY0NWEwMTBiMTIwYzQ5MGY3MDAzMGY3OTA3ODg3MDYzMGFlNWU0ZjFiMGZhNTA0NjBlMmZiMWFiMGY2ZDcwIiwic2lnbmF0dXJlX3NoYTI1NiI6IjljNzAzNTFkMWQ2ODY5NTQ0MGE1MThmYjJkM2VhNzgxZWQzY2RiNWU0NTRiNjQ3ZDg1NTNiNGJjYWM1YzkzNzgifQ -->
### `client.analysis.analyzeContractDrift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  
Equivalent member: `client.analyzeContractDrift`  

#### Signature

```javascript
client.analysis.analyzeContractDrift(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.analysis.analyzeContractDrift({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplUGVyZkZpbk9wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiI4YmU3NzZiOTUxMTk3ODU1NzBiOWIxNzQ3NTkyMDEwMDAxNDE1YzZlYzEzZWI1ZDFlZjBiMjQxYTk2NDEwZTRkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjMyZGUwNDljNmJlMzIzM2Y3MDc2OTFjMmE2NDE5NTA2YTMyOWVlOWY3OWQxZDczYzZmZTE5ZmZiNzEzNjVjYWUifQ -->
### `client.analysis.analyzePerfFinOps`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  
Equivalent member: `client.analyzePerfFinOps`  

#### Signature

```javascript
client.analysis.analyzePerfFinOps(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.analysis.analyzePerfFinOps({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuU3RhY2tlZFByU3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImI0ODM1YTI1MzAwMzIyYzU1MjY4MmQ1Y2U3ZWU5NDdjNTU3ZjUzNzk3M2MxMTNjYWFkOTI4N2Y3NDA2OGVjMTkiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjA4NWZkZDhmZWI2MDM0NDAxZTYzYzEyZmQzNTBlZDEyNmRlNGQ5MjYxNTM0ZWUxM2Q5NDVmOWUyYTkzYzEzZSJ9 -->
### `client.analysis.planStackedPrSplit`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  
Equivalent member: `client.planStackedPrSplit`  

#### Signature

```javascript
client.analysis.planStackedPrSplit(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.analysis.planStackedPrSplit({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0Um9pIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QW5hbHl0aWNzUm9pIiwicGF0aCI6Ii92MS9hbmFseXRpY3Mvcm9pIiwicmVzb3VyY2UiOiJhbmFseXRpY3MiLCJzZWN0aW9uX3NoYTI1NiI6ImFjMzQ3MjBlNGU4MzQyNjEzM2Y0MjdhZWYyM2Y3OGRkN2JhMGE3YjYzYzllMDZkYWVlYjdjNjhiYTU5YWE1MTkiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmRkMmQwYTNhODk3ZWNkYzIwMDVlZjQ0OTYzYjFiNDYyYmFjZjg0ODFlOWJiMWM4YmFmYzFlMmQwZDY3NDllZSJ9 -->
### `client.analytics.getRoi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  
Equivalent member: `client.getAnalyticsRoi`  

#### Signature

```javascript
client.analytics.getRoi(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.analytics.getRoi();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiNDk5NGZiOThiNGJhMTg2MGQ4YWMyYmQ2NGY1OWQ3ZDU2MTI0Y2VlOTk3ZmY5ZmRhZTIzNjVmMWQyYjJmZTQ0MSIsInNpZ25hdHVyZV9zaGEyNTYiOiI2YzE5Y2ZkOTg2ZmM4YjNiMGYzYTk1MmU5ODcyMDNlY2M1YzUzNmFhMmY0MWQzZTBhMDUwZWU3Y2UwOWE4MDMxIn0 -->
### `client.capabilities.get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  
Equivalent member: `client.getCapabilities`  

#### Signature

```javascript
client.capabilities.get(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.capabilities.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlR2F0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL2dhdGUiLCJyZXNvdXJjZSI6ImNvbXBsaWFuY2UiLCJzZWN0aW9uX3NoYTI1NiI6ImYzMjFhN2Q4NWFkYmQ5YTFjYjUxNmU1YWYzODkyNjEwYjg4MTViOGVlNTMzNWMyMjdjN2ExMWQ3MzQ5YTQ1MjQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMTBkYTExMzg1MDY1NDAzYzllN2UyMTlhNmNiMTVjMTE2ODBlYTZjNmJkYzBkOTRkMDhmYTQ2MzJlMGUxMGM2YiJ9 -->
### `client.compliance.evaluateGate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  
Equivalent member: `client.evaluateComplianceGate`  

#### Signature

```javascript
client.compliance.evaluateGate(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.compliance.evaluateGate({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydFNhcmlmIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImV4cG9ydFNhcmlmIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL3NhcmlmIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI2Y2ViN2VhZjY1MTIwODAwMzdjZDRiZmIwMWFlNjAwNTgxODI2ZmZmMjM0M2E5NTA4M2Y0YmVhODM1MmZhZWNmIiwic2lnbmF0dXJlX3NoYTI1NiI6IjVmZmZlZjZjMTEyYjg5N2RjZjcyNDU5YzgwNDZjNDIxNGY3MDBmMWRlMjFmYTBkMzFiMTBiYjkxMGJiMDk0MWYifQ -->
### `client.compliance.exportSarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  
Equivalent member: `client.exportSarif`  

#### Signature

```javascript
client.compliance.exportSarif(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.compliance.exportSarif({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `developerIntelligence`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuY29sbGVjdEF1ZGl0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNvbGxlY3REZXZlbG9wZXJBdWRpdCIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWF1ZGl0IiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjQxMGJhMzcxMzM4YWRkOWQyNTk5ZWU1ODMwOGY1YzFmNTUyYzE2OTBhMThmNmI0NjNjNDA1NjY5YTJlMDhmYmUiLCJzaWduYXR1cmVfc2hhMjU2IjoiODBlMDIxN2Y0YzI3ODI3N2E3MTQ2NDVhOWYyOTU5ZjRjZGY3ZmRmZDlkY2E2NjQwNTkzOGE3OWUxNTdiMzFjZSJ9 -->
### `client.developerIntelligence.collectAudit`

Operation ID: `collectDeveloperAudit`  
Route: `POST` `/cli/managed/developer-audit`  
Equivalent member: `client.collectDeveloperAudit`  

#### Signature

```javascript
client.developerIntelligence.collectAudit(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperAuditRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Versioned report with source coverage, missing evidence and immutable snapshot reference. | application/json (object) |
| `default` | Explicit authentication, paid access, source authorization, capacity or collection blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "from": "2026-01-09",
    "repositoryId": "1",
    "to": "2026-01-18"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.collectAudit({"from": "2026-01-09", "repositoryId": "1", "to": "2026-01-18"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb2xsZWN0RGV2ZWxvcGVyQXVkaXQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuY3VycmVudElkZW50aXR5IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImN1cnJlbnREZXZlbG9wZXJJZGVudGl0eSIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWlkZW50aXR5IiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6ImQzN2M5MWQ2MTZlNzBmNGYzMzc2Mzg5MzQ1NGY0NzY4ZDYxMmViYzMzNmU0ZmY4YjYzNjc3ZGFlYWYwNWJkZmYiLCJzaWduYXR1cmVfc2hhMjU2IjoiOGNkMGQwZmFlNmVkNjAwYzY4MWI3NjUyZWYwNGI4YmFiMGVkOWNhZTk4ZjU4ZGQzNDM5M2I4M2I3MGE5ZjYyMSJ9 -->
### `client.developerIntelligence.currentIdentity`

Operation ID: `currentDeveloperIdentity`  
Route: `POST` `/cli/managed/developer-identity`  
Equivalent member: `client.currentDeveloperIdentity`  

#### Signature

```javascript
client.developerIntelligence.currentIdentity(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ManagedDeveloperIdentityRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Current verified identity and authorized repositories. | application/json (ManagedDeveloperIdentity) |
| `default` | Explicit account, GitHub identity or source authorization blocker. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.currentIdentity({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjdXJyZW50RGV2ZWxvcGVySWRlbnRpdHkifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuZGVjbGFyZVByb2plY3RDb250ZXh0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImRlY2xhcmVEZXZlbG9wZXJQcm9qZWN0Q29udGV4dCIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtY29udGV4dCIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI5NGU3ZWVjM2RkODE0M2Y0ZjVkZjRlMTc1YWY1YThmMGU4NzdlNWYwNWJlNjQwYmRmZjE4Yzg5YThmOTY5MDkzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjQ2MzNiYTM0NTQ2M2YwYTA4ZmI3OWQyZGZkZjk3ZWU0NDYzNTI2ZjViMGEzNmEzOWI3MjUyNDAzOWIxNjVjMjcifQ -->
### `client.developerIntelligence.declareProjectContext`

Operation ID: `declareDeveloperProjectContext`  
Route: `POST` `/cli/managed/audit-context`  
Equivalent member: `client.declareDeveloperProjectContext`  

#### Signature

```javascript
client.developerIntelligence.declareProjectContext(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditContextRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Immutable declaration or correction receipt. | application/json (object) |
| `default` | Explicit authorization, contributor identity, correction or storage capacity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "declaration": {
      "contributorId": "1",
      "effectiveFrom": "2026-01-02",
      "effectiveTo": "2026-01-11",
      "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "source": "example",
      "supersedes": "example",
      "type": "project_join",
      "value": "example"
    },
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.declareProjectContext({"declaration": {"contributorId": "1", "effectiveFrom": "2026-01-02", "effectiveTo": "2026-01-11", "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa", "source": "example", "supersedes": "example", "type": "project_join", "value": "example"}, "repositoryId": "1"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJkZWNsYXJlRGV2ZWxvcGVyUHJvamVjdENvbnRleHQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UubWFuYWdlZEF1ZGl0U25hcHNob3RzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Im1hbmFnZWRBdWRpdFNuYXBzaG90cyIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtc25hcHNob3RzIiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6ImIxNTk3OTBiMmM1YTM2NWRjZTVkYjE1ZDY2MTQ5NTY2ZjExZGY4ZDAwZmRhYjg5YmIwNzg3ZjcyMzNjYjM1MjMiLCJzaWduYXR1cmVfc2hhMjU2IjoiYWMyNjgyMjhlY2I2MGE3MmJhNDZlZGEwMGJkYTZiMjQzMzRlNjE3MmJiMTFhOWFlNDUzZDJiYjkxYjI2ZGI5YyJ9 -->
### `client.developerIntelligence.managedAuditSnapshots`

Operation ID: `managedAuditSnapshots`  
Route: `POST` `/cli/managed/audit-snapshots`  
Equivalent member: `client.managedAuditSnapshots`  

#### Signature

```javascript
client.developerIntelligence.managedAuditSnapshots(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditSnapshotsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot list or digest-verified immutable envelope. | application/json (object) |
| `default` | Explicit authorization, expiry, missing snapshot or integrity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "list",
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.managedAuditSnapshots({"action": "list", "repositoryId": "1"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJtYW5hZ2VkQXVkaXRTbmFwc2hvdHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UucHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2Zpbm9wcyIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI3ZWJiYmQ5ZjgzZjNmOTQyOWU5OTcxZDMwNDI2OGY0YmFlZmRhNDhkOTBiMzE3Y2I2N2YzMjhjNjY0ZTk5Njg0Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImE2ZTcyNzU0NTMwOGI1M2YyM2NiNjJkZTQ1MzUwODMxMWJhZGE4MjFmOTA3MWM2YTMwYTMzNDc2NDQ5ZWFmNzgifQ -->
### `client.developerIntelligence.providerCostEvidence`

Operation ID: `providerCostEvidence`  
Route: `POST` `/cli/managed/finops`  
Equivalent member: `client.providerCostEvidence`  

#### Signature

```javascript
client.developerIntelligence.providerCostEvidence(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `FinOpsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server report or declaration receipt. Unknown costs remain null. | application/json (object) |
| `default` | Explicit permission, paid access, source or declaration validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "report"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.providerCostEvidence({"action": "report"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aWRlckNvc3RFdmlkZW5jZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2Uuc3VibWl0RXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3VibWl0RGV2ZWxvcGVyRXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2RldmVsb3Blci1ldmlkZW5jZSIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJkYjk0MTNhYTViNThlOTBiMmNmZTk4ODAxZjlhZDVkZGZmMWNhNDUyOWRhMzQwNTg0YTA1NmQ0OGFiZGNjOTI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImZiYzMzNThmYzJjMzc4NTFjZjhkNTkwMzU5YTU4YjNhNWQ4MThhZTY3OTdmMmE2NDIyOTc2OWRkZTgxNTE1YjgifQ -->
### `client.developerIntelligence.submitEvidence`

Operation ID: `submitDeveloperEvidence`  
Route: `POST` `/cli/managed/developer-evidence`  
Equivalent member: `client.submitDeveloperEvidence`  

#### Signature

```javascript
client.developerIntelligence.submitEvidence(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperEvidenceRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Accepted and duplicate span counts. | application/json (object) |
| `default` | Explicit identity, repository, paid access or evidence validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "category": "coding",
    "input": {},
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.developerIntelligence.submitEvidence({"category": "coding", "input": {}, "repositoryId": "1"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXREZXZlbG9wZXJFdmlkZW5jZSJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiYjdlMTUzMGI4Y2VkNWY4ODY5Mjc4MmVkNzVmMWU1YzVkYTIwYmFiNGMwYTg0M2UyMDk2MDU4NTZkNjEwMzNjZSIsInNpZ25hdHVyZV9zaGEyNTYiOiIwMjQzZWEwOTU4OTg0OTI2YjYzNWU5NjU5MDVmYzE2ZWQ0OWE5OWVmMjY4ZDExM2ZiNWZhYzFhN2E2Mjk4MDVmIn0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.getHealth`  

#### Signature

```javascript
client.health.get(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.health.get();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkQXV0b2ZpeEJ1bmRsZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiMWQxMzVmYTRlMjFmMjE0OTMzZjVmYWYyNmEzZjQzOWQ4OTk5Zjg3MTViZTJlZTc0OGJiNmI5MTMxZDFkOTg3ZSIsInNpZ25hdHVyZV9zaGEyNTYiOiJhNzVjZDUxMGUxNWVhZGIwNzA3NzZjZDFhNmFjMmU5ZTJjMDJlMTYxYzE5NzJmZTNhZGUyOTMxN2E5ZTY0YWFiIn0 -->
### `client.reviews.buildAutofixBundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  
Equivalent member: `client.buildAutofixBundle`  

#### Signature

```javascript
client.reviews.buildAutofixBundle(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.reviews.buildAutofixBundle({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVSaXNrUmFkYXIiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiI5YThkNDc5NDYzOGM0ZDFkYWNiMjQ5MzYzZWE4MzYxNTBhNDY4NTFlNDdmMzllZTJjZWY0ZmM4MDI5OTViNzVhIiwic2lnbmF0dXJlX3NoYTI1NiI6IjA5NDAzMjkyZDYwZDI2MDY3YThiNzRkNmY5N2M3MTMxZDg0ZTZlZGIyNTVkZTkyOGNlYTNkZTI1YTg2MDFkY2IifQ -->
### `client.reviews.computeRiskRadar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  
Equivalent member: `client.computeRiskRadar`  

#### Signature

```javascript
client.reviews.computeRiskRadar(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.reviews.computeRiskRadar({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImJjOTU4YjM5YmRmZDQ5MTJhZDliYzdjYWY1MmU0MzAyYWExYjU0ZjhkYmNkMjJkZmI5YjM3MDhjNjM4YWJmZTQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMzM3ZDUwY2Y3OTRlNWU0MzYwM2Y3Y2Y1Y2YxMDJlMmQzMGE1MmMxNmRjZmZlMjc2NWM4M2YwZGU2NTBlODNlNSJ9 -->
### `client.reviews.create`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  
Equivalent member: `client.createReview`  

#### Signature

```javascript
client.reviews.create(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.reviews.create({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplTWV0ZXJpbmdRdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjBlMTMyZTJmMWVjNzNjYzYzMzFiMjJjNzBlNzdjZWY3MTMyNTM4Y2IwZTY2ZGEwNjQzOWRmOWQ0MThhMjkxYjciLCJzaWduYXR1cmVfc2hhMjU2IjoiODg2NjcwYjllZTAwZTEzMTBmZWE5OTliYWRjYWFlZWNlMWIyYmFlNWYwOTZiOTI0OTA5Mjc1ZGE2ZGQxYmE0NCJ9 -->
### `client.saas.finalizeMeteringQuota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  
Equivalent member: `client.finalizeMeteringQuota`  

#### Signature

```javascript
client.saas.finalizeMeteringQuota(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.saas.finalizeMeteringQuota({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldEJsdWVwcmludCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFNhYXNCbHVlcHJpbnQiLCJwYXRoIjoiL3YxL3NhYXMvYmx1ZXByaW50IiwicmVzb3VyY2UiOiJzYWFzIiwic2VjdGlvbl9zaGEyNTYiOiJiMTk5ZGE3MmU2M2I5ZTRjMmFhNTZkMDlkZDJmZWRlYzQ0NmExMDI4ZDhkY2I3Y2EyYmU5MDEwZDQ1OGMyYmE5Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjgxN2I3ZDFjNWU1OWZlZTM1ODdmNjE3NGUxNDJjYmFhYzAzMzgyYTVkZmNmZGJlNGIyMGI3YTZlMWJiYTllNmMifQ -->
### `client.saas.getBlueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  
Equivalent member: `client.getSaasBlueprint`  

#### Signature

```javascript
client.saas.getBlueprint(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.saas.getBlueprint();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlU3VyZmFjZUxlYXNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjY2ZWIyNjM1Yzc0MTcyMTI2ODRjMjVhOTU4ZDhiM2E0ZTRjY2M2NmYwNjc1Y2QyZGQwZDRiM2I0NjIxOTI5ZWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWVkNTdlMDlkZmRhOGJlM2FlMmFjN2NjNjQ1YWE4ZmVjOTU0MDZhZjNiOWY0YmQ1M2Q0MGY0YWQ0NTNiYTVkMCJ9 -->
### `client.saas.issueSurfaceLease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  
Equivalent member: `client.issueSurfaceLease`  

#### Signature

```javascript
client.saas.issueSurfaceLease(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.saas.issueSurfaceLease({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVNZXRlcmluZ1F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImNlM2JkYjVjOTU5YzIxMzY3NjlkNjgzNmY0NzQ4ZjcwMDI2ZjVkNDNmN2FhZWJhNjM0NDNmMzE3MTUyNTE4MDYiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmU3YWQxYzAwMGNkOTdhYzlmYTI2ZmRlNzg3MmI0NGM0NTA2NzMwNThjYjVmZTc4OTFlNWQyMmFiYmU3YzUwNSJ9 -->
### `client.saas.reserveMeteringQuota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  
Equivalent member: `client.reserveMeteringQuota`  

#### Signature

```javascript
client.saas.reserveMeteringQuota(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.saas.reserveMeteringQuota({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiZDYzMmQ5MjA5ZDgyYzFlY2RkYTIzZjRkN2IxOWRiNmJlMGJhOThlNjdjNTA2YmVhZTA5MDQ5ZThlMmMxOTA2NiIsInNpZ25hdHVyZV9zaGEyNTYiOiIxNGU3MWYyODM4MjAwNTY0MDU2NDNiMGY0MzY2MTZjMGVhMmFmZTE1YzY1MzQ5MGQwNzlmN2E0OTgzODg4NjJlIn0 -->
### `client.sbom.generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  
Equivalent member: `client.generateSbom`  

#### Signature

```javascript
client.sbom.generate(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.sbom.generate({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supplyChain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlDaGFpbi5hbmFseXplIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVTdXBwbHlDaGFpbiIsInBhdGgiOiIvdjEvc3VwcGx5LWNoYWluL2FuYWx5emUiLCJyZXNvdXJjZSI6InN1cHBseUNoYWluIiwic2VjdGlvbl9zaGEyNTYiOiIxNzI1M2E1YjdkMmJmYmQyMTA0ZWIyZTQ2ZDIxYjZkYWYxNDQ2MjUwZGQ2MjYwZDIzZGNmMDhlOTE0OTljZTQxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjFkYjQ5ZmZmYzM3YzIyMzlmODE3MWQzMzQyNjYwODAzYWQ5NDIxZDAxMDM4Yjk2YjNkYjZkOGEyOWE5NjgzOTYifQ -->
### `client.supplyChain.analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  
Equivalent member: `client.analyzeSupplyChain`  

#### Signature

```javascript
client.supplyChain.analyze(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.supplyChain.analyze({"files": [{"filename": "example"}]}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVDb2RpbmciLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiIwY2Q2YTdjZTg1YzI2Mzc1ZDA1MzMxNmE5NjhhYmNjMzlmN2YzZWQzYzRiZDFhMjY5YmE4MDMyMGE1OWE5YjNjIiwic2lnbmF0dXJlX3NoYTI1NiI6Ijk0OGQxM2NlMTA0MTA5YjUxMWViZGZiZDhjNmY0OGZmMmU4MzUyODE0NDhhZDAzOTIzM2JiODIwNDE3N2VkZDQifQ -->
### `client.tasks.createCoding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  
Equivalent member: `client.createCodingTask`  

#### Signature

```javascript
client.tasks.createCoding(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.tasks.createCoding({}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0Q29kaW5nIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdENvZGluZ1Rhc2tzIiwicGF0aCI6Ii92MS90YXNrcyIsInJlc291cmNlIjoidGFza3MiLCJzZWN0aW9uX3NoYTI1NiI6IjlkNjYwMTY5ZmQxNjc2ZjZmN2M4MDY4MjE1MjBmNDM0NmZhYWI0OTk2NGU1MDVjMjFiZTdjOGU4NTI3NDM2NzUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZWU4YjhjYzUyNDZlY2JhMmYyZWM1YjdhYTAwM2EzMTA1MDc2OGZkNjVhZDE4YTkzOTlkMTIyMGQyMjViZTBlYiJ9 -->
### `client.tasks.listCoding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  
Equivalent member: `client.listCodingTasks`  

#### Signature

```javascript
client.tasks.listCoding(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.tasks.listCoding();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0UXVldWUiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSIsInBhdGgiOiIvdjEvdHJpYWdlIiwicmVzb3VyY2UiOiJ0cmlhZ2UiLCJzZWN0aW9uX3NoYTI1NiI6IjEwNmRkMTc1MGIyYmIzMmNjOWQzZGY1NDBhNjYzYjBjYWZmZjc4MWM5ZDNhOTYyNjI1MGRiMjc1M2YxM2MxOGQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjJlY2RjYmMwNDk4ODBiMmYxNmM1MDVlNWUyNWRkZTUwNWQxNmVhM2NlOWY2M2UxOWEzNjkwZjgyMDdmZjdhNSJ9 -->
### `client.triage.getQueue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  
Equivalent member: `client.getTriageQueue`  

#### Signature

```javascript
client.triage.getQueue(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.triage.getQueue();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6Ijk4ZGZhNTI3OTk3NWI1MTMyMmE2ZmI4YzdlY2Q5MGFkNmU1Mzk5MmQ4NGUwNDdjNWQwNGE0NWNiNjYyNTEzZjgiLCJzaWduYXR1cmVfc2hhMjU2IjoiNTJlNDhjMmNlNGEzZGU4YzYxOWJlZWY0MDJjMzFhYjIzYTI5ZDRiYjBjZDczMzRmMjNhNzdkZTg3MjZhMWE2MyJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.listWaitlist`  

#### Signature

```javascript
client.waitlist.list(requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.waitlist.list();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6ImU3ZjFmMTIwYzBiNDMyMGVkYWJiNTIxYzk1YzcwMjNlODRhZjE0Y2M0YmFhZTk1NGYxNDZjMGEwMjE3NjdjNGYiLCJzaWduYXR1cmVfc2hhMjU2IjoiYzdjOWY4ZTcwZWE4ODhhYmYxMzkxNzAwYTIxYTU3NTAxNDdkYjYyNzQ2Y2Y5ZDY1YjUxM2VlM2ZhOThhOTgxYiJ9 -->
### `client.waitlist.register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.registerWaitlist`  

#### Signature

```javascript
client.waitlist.register(body, requestOptions?)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```javascript
const result = await client.waitlist.register({"email": "example-c65f@example.test"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

