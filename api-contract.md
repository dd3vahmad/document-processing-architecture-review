# Document Processing API Contract

## Endpoint

`POST /documents/process`

### Request

`Content-Type: application/json`

    {
      "documentId": "doc-001",
      "idempotencyKey": "request-001"
    }

### Current behavior under review

The endpoint performs document processing during the HTTP request. Some processing attempts may exceed the configured request timeout.

### Candidate queued behavior

For a valid request accepted for background processing:

- Return `202 Accepted`.
- Return a unique job ID.
- Include a status URL, such as `/jobs/{jobId}`.
- Allow the client to retrieve job status separately.

### Candidate status endpoint

`GET /jobs/{jobId}`

Possible states:

- `queued`
- `processing`
- `completed`
- `failed`

### Error behavior

- Invalid requests should receive a clear client error.
- A duplicate idempotency key should refer to the existing logical request.
- Temporary worker failures may be retried according to a bounded retry policy.
- Permanent failures should become visible and recoverable through an operational process.

### Open contract decisions

- Exact request timeout and response schema.
- Idempotency key scope and retention.
- Retry limits and backoff.
- Queue durability and dead-letter handling.
- Authorization for status and result retrieval.
