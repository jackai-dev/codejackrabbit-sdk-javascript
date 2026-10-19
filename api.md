# CodeJackRabbit JavaScript API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImZlMGYyMjU1OGZiNDM0MTEwODJkZjVlMDc2MmEyM2U5ZWFmOTBhOWM3MTNmZTRlZTljZmQyNzM3OTIyMjgwM2QiLCJvcGVyYXRpb25fY291bnQiOjIyLCJyZW5kZXJlciI6ImphdmFzY3JpcHQiLCJ2ZXJzaW9uIjoiMS40LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `fe0f22558fb43411082df5e0762a23e9eaf90a9c713fe4ee9cfd27379222803d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **verified**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new Client({ hooks })` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. `beforeRequest` is the one hook that may change the request (the documented per-request credential contract, which also reads credentials masked); the other three receive frozen `HookContext` copies.

`new Client({ tracer })` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ComplianceGateRequest`
- `FileChange`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplQ29udHJhY3REcmlmdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCIsInBhdGgiOiIvdjEvYW5hbHlzaXMvY29udHJhY3QtZHJpZnQiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiJjZDQ3NjRkZTM4ODQ2Y2QyOWI1M2M3NGFlM2M2ZGUzYmI3Y2IyYzUwZGJiN2JiOTc1ZWU2N2Q1NTcwNWVkNTY3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjljNzAzNTFkMWQ2ODY5NTQ0MGE1MThmYjJkM2VhNzgxZWQzY2RiNWU0NTRiNjQ3ZDg1NTNiNGJjYWM1YzkzNzgifQ -->
### `client.analysis.analyzeContractDrift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplUGVyZkZpbk9wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiI2NTI4MTFlYTVmOGI1MGU2NDFiY2U0ZmY1NzQ5Y2I0YTRkNjIzZjVjZDMzMGY4NGFjY2ViMGQwYTE2N2EyM2ZlIiwic2lnbmF0dXJlX3NoYTI1NiI6IjMyZGUwNDljNmJlMzIzM2Y3MDc2OTFjMmE2NDE5NTA2YTMyOWVlOWY3OWQxZDczYzZmZTE5ZmZiNzEzNjVjYWUifQ -->
### `client.analysis.analyzePerfFinOps`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuU3RhY2tlZFByU3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImQ1ZGQ4ODUyNDdjNzJjMzA2ODdkZmNkZmQ4YzMzNGVhYWNlNmEzMTNjM2U1OTY5MzEwNzVlNTk3NGJhZmY2OTQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjA4NWZkZDhmZWI2MDM0NDAxZTYzYzEyZmQzNTBlZDEyNmRlNGQ5MjYxNTM0ZWUxM2Q5NDVmOWUyYTkzYzEzZSJ9 -->
### `client.analysis.planStackedPrSplit`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0Um9pIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QW5hbHl0aWNzUm9pIiwicGF0aCI6Ii92MS9hbmFseXRpY3Mvcm9pIiwicmVzb3VyY2UiOiJhbmFseXRpY3MiLCJzZWN0aW9uX3NoYTI1NiI6IjhhYTEyZTVlMTcwNDFlYTU4M2JlMjdlODc2YjRlZDgzMThiZDJiYTNmMDhlMjk1NDFmMjcyMDY3ZGMxZjUyY2IiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmRkMmQwYTNhODk3ZWNkYzIwMDVlZjQ0OTYzYjFiNDYyYmFjZjg0ODFlOWJiMWM4YmFmYzFlMmQwZDY3NDllZSJ9 -->
### `client.analytics.getRoi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiNjUyMTM1OTM2YTc5YjY0MzkyNTU3YzllYWQ1ZjhmNTMwNmMxNTg3MWUxMDk1MGMyZThlNzE0YzE0N2E2YzlhMCIsInNpZ25hdHVyZV9zaGEyNTYiOiI2YzE5Y2ZkOTg2ZmM4YjNiMGYzYTk1MmU5ODcyMDNlY2M1YzUzNmFhMmY0MWQzZTBhMDUwZWU3Y2UwOWE4MDMxIn0 -->
### `client.capabilities.get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlR2F0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL2dhdGUiLCJyZXNvdXJjZSI6ImNvbXBsaWFuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjdiNmMzMWVjNTYwZmZhNjdhYjIyNTEyZTg3NDcwZmY4ZjVkZDU3YThmMDZiMzYxYzMyMGVlNDY5NTZkMjM4YWYiLCJzaWduYXR1cmVfc2hhMjU2IjoiMTBkYTExMzg1MDY1NDAzYzllN2UyMTlhNmNiMTVjMTE2ODBlYTZjNmJkYzBkOTRkMDhmYTQ2MzJlMGUxMGM2YiJ9 -->
### `client.compliance.evaluateGate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydFNhcmlmIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImV4cG9ydFNhcmlmIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL3NhcmlmIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI5YTViNTI3ZTExMThiMThhY2ZiMGUxZjU4NjNhZjI5ODBlMDE5ZTZlMmFkOGY2MjBiMWQ5YzFjMjE1MjU2OWI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjVmZmZlZjZjMTEyYjg5N2RjZjcyNDU5YzgwNDZjNDIxNGY3MDBmMWRlMjFmYTBkMzFiMTBiYjkxMGJiMDk0MWYifQ -->
### `client.compliance.exportSarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

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

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiODNiYWE0ZWEwMDY1ZDlhNTY0YmRhYmJiMjhhNTFhNTllN2JkMmY5NDY2NjNiZTViYWIzZDMwYTE5NDJlZWEwMCIsInNpZ25hdHVyZV9zaGEyNTYiOiIwMjQzZWEwOTU4OTg0OTI2YjYzNWU5NjU5MDVmYzE2ZWQ0OWE5OWVmMjY4ZDExM2ZiNWZhYzFhN2E2Mjk4MDVmIn0 -->
### `client.health.get`

Operation ID: `getHealth`  
Route: `GET` `/health`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkQXV0b2ZpeEJ1bmRsZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiNmIyZWFlMDRiMzljNGQ1ZGViNDIzNzRkNzY1MTI3OTg1NGQ1NjEzOGZkMjRmMmVjZDYwMzhiNmY2MzdmMTk3YyIsInNpZ25hdHVyZV9zaGEyNTYiOiJhNzVjZDUxMGUxNWVhZGIwNzA3NzZjZDFhNmFjMmU5ZTJjMDJlMTYxYzE5NzJmZTNhZGUyOTMxN2E5ZTY0YWFiIn0 -->
### `client.reviews.buildAutofixBundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVSaXNrUmFkYXIiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiIzZTJhZGVlYjNmMDk0YjY2ZTUxNGE0MzIyNjUxMmMzNTQwY2JhOTczYjhlZTRhYjczMjAzZTcwMDZmMGI3ODIyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjA5NDAzMjkyZDYwZDI2MDY3YThiNzRkNmY5N2M3MTMxZDg0ZTZlZGIyNTVkZTkyOGNlYTNkZTI1YTg2MDFkY2IifQ -->
### `client.reviews.computeRiskRadar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImUzY2UwZDFhZDUwMDMxZTQ3MTBmMGM2MmEyZGNlZDlmODk2NDM0MmZkNDU3OTJiMGUxMTJhNTYzYTVkZjEzZjkiLCJzaWduYXR1cmVfc2hhMjU2IjoiMzM3ZDUwY2Y3OTRlNWU0MzYwM2Y3Y2Y1Y2YxMDJlMmQzMGE1MmMxNmRjZmZlMjc2NWM4M2YwZGU2NTBlODNlNSJ9 -->
### `client.reviews.create`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplTWV0ZXJpbmdRdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImQ0Y2Q4YjhhYTQ5ZTllZGFjZjA5YmZlNDE0OTE0NjhhZWI5NjU1ZGZiN2M3ZWM3YzBhMDA5YjljOGU5NjM0YTIiLCJzaWduYXR1cmVfc2hhMjU2IjoiODg2NjcwYjllZTAwZTEzMTBmZWE5OTliYWRjYWFlZWNlMWIyYmFlNWYwOTZiOTI0OTA5Mjc1ZGE2ZGQxYmE0NCJ9 -->
### `client.saas.finalizeMeteringQuota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldEJsdWVwcmludCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFNhYXNCbHVlcHJpbnQiLCJwYXRoIjoiL3YxL3NhYXMvYmx1ZXByaW50IiwicmVzb3VyY2UiOiJzYWFzIiwic2VjdGlvbl9zaGEyNTYiOiJhNWE2MTNiZGU0NmE0NzE0MjU5OWE4OTFlZDc5YzA4YzNkOThkYWExNDI4ZWY1ZDNkYWY2YWRlMjVjMjE3MzU5Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjgxN2I3ZDFjNWU1OWZlZTM1ODdmNjE3NGUxNDJjYmFhYzAzMzgyYTVkZmNmZGJlNGIyMGI3YTZlMWJiYTllNmMifQ -->
### `client.saas.getBlueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlU3VyZmFjZUxlYXNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjA1YTkyYWQxNGFlMmZhNjE0NjM4MzUxNTExZGQ3NTBiMTYyNTA3YWJlMmM3OGQ0MjBiY2ZkNzFlNjhlMmMyYjciLCJzaWduYXR1cmVfc2hhMjU2IjoiOWVkNTdlMDlkZmRhOGJlM2FlMmFjN2NjNjQ1YWE4ZmVjOTU0MDZhZjNiOWY0YmQ1M2Q0MGY0YWQ0NTNiYTVkMCJ9 -->
### `client.saas.issueSurfaceLease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVNZXRlcmluZ1F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImM4NDNiNjlhNDdkYjk3YjE0YzZiMDM4ZDA4N2YzMzYxZWIxYzIzOTY1ZmY5YmE2MTEyOGEwZWEzZGI2ZjgwZDMiLCJzaWduYXR1cmVfc2hhMjU2IjoiMmU3YWQxYzAwMGNkOTdhYzlmYTI2ZmRlNzg3MmI0NGM0NTA2NzMwNThjYjVmZTc4OTFlNWQyMmFiYmU3YzUwNSJ9 -->
### `client.saas.reserveMeteringQuota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImdlbmVyYXRlU2JvbSIsInBhdGgiOiIvdjEvc2JvbSIsInJlc291cmNlIjoic2JvbSIsInNlY3Rpb25fc2hhMjU2IjoiMmVhMjE1ZWQ4YmI1NzFiNjBhODNjYmI3Yjg0MGQyMTVhNmNjOTNmYTliOTFlZTU4MmRkNjhlY2U2ZDQ5MjEyZiIsInNpZ25hdHVyZV9zaGEyNTYiOiIxNGU3MWYyODM4MjAwNTY0MDU2NDNiMGY0MzY2MTZjMGVhMmFmZTE1YzY1MzQ5MGQwNzlmN2E0OTgzODg4NjJlIn0 -->
### `client.sbom.generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlDaGFpbi5hbmFseXplIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVTdXBwbHlDaGFpbiIsInBhdGgiOiIvdjEvc3VwcGx5LWNoYWluL2FuYWx5emUiLCJyZXNvdXJjZSI6InN1cHBseUNoYWluIiwic2VjdGlvbl9zaGEyNTYiOiJiZTY5YjBhNWE5MzVjNTFiMDYyZWQ1MzVmNDU4ZGM3ZDBjZWU2ZWVhZjdmYjc3YjIwYTRkMTU3Yjk5MWVkNTVjIiwic2lnbmF0dXJlX3NoYTI1NiI6IjFkYjQ5ZmZmYzM3YzIyMzlmODE3MWQzMzQyNjYwODAzYWQ5NDIxZDAxMDM4Yjk2YjNkYjZkOGEyOWE5NjgzOTYifQ -->
### `client.supplyChain.analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVDb2RpbmciLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6InRhc2tzIiwic2VjdGlvbl9zaGEyNTYiOiI1N2ZhZjEzYTdlNGQyNjgzNmU1MDlkZWYxMTI4ZTJiN2Y1ZjYzYTZkZDdkMjY5ZTNmNDBkODY3NGFhMzNjMTA4Iiwic2lnbmF0dXJlX3NoYTI1NiI6Ijk0OGQxM2NlMTA0MTA5YjUxMWViZGZiZDhjNmY0OGZmMmU4MzUyODE0NDhhZDAzOTIzM2JiODIwNDE3N2VkZDQifQ -->
### `client.tasks.createCoding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0Q29kaW5nIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdENvZGluZ1Rhc2tzIiwicGF0aCI6Ii92MS90YXNrcyIsInJlc291cmNlIjoidGFza3MiLCJzZWN0aW9uX3NoYTI1NiI6IjAyNDNkYjVlODQ5YTE1OTIzN2RmZWQwZDQ3ZWE5NTVjOTFlYThlMDMxMzI1MDA5OTI2YTlmMWU4MDNlMmNkODkiLCJzaWduYXR1cmVfc2hhMjU2IjoiZWU4YjhjYzUyNDZlY2JhMmYyZWM1YjdhYTAwM2EzMTA1MDc2OGZkNjVhZDE4YTkzOTlkMTIyMGQyMjViZTBlYiJ9 -->
### `client.tasks.listCoding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0UXVldWUiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSIsInBhdGgiOiIvdjEvdHJpYWdlIiwicmVzb3VyY2UiOiJ0cmlhZ2UiLCJzZWN0aW9uX3NoYTI1NiI6ImJiZDdjYzRiMzVjMDUwMzI3ZmVkYjZkYjU1NzNkODRhOGQ2OGExZWU0M2ExNzNjN2YyMjVjMTM2OGFiMzAwYTgiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjJlY2RjYmMwNDk4ODBiMmYxNmM1MDVlNWUyNWRkZTUwNWQxNmVhM2NlOWY2M2UxOWEzNjkwZjgyMDdmZjdhNSJ9 -->
### `client.triage.getQueue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6ImZhNmU2NTVjNzg0YjJjZDU3NTg1NjExMWEzMjUxYWMxY2JjMmFkMjk0MzllZTA2NDdlNzA3M2Q0NTJjOTYzNmMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNTJlNDhjMmNlNGEzZGU4YzYxOWJlZWY0MDJjMzFhYjIzYTI5ZDRiYjBjZDczMzRmMjNhNzdkZTg3MjZhMWE2MyJ9 -->
### `client.waitlist.list`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

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

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoid2FpdGxpc3QiLCJzZWN0aW9uX3NoYTI1NiI6IjcyYWRkYTAzYjE2NTYxNzZhYTJhNmNiNTIwNTk1YTkyZmNkYjk3ZjhhZmU0ODFiMTQzN2RmMjg0ODc0NzNlNTgiLCJzaWduYXR1cmVfc2hhMjU2IjoiYzdjOWY4ZTcwZWE4ODhhYmYxMzkxNzAwYTIxYTU3NTAxNDdkYjYyNzQ2Y2Y5ZDY1YjUxM2VlM2ZhOThhOTgxYiJ9 -->
### `client.waitlist.register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

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

