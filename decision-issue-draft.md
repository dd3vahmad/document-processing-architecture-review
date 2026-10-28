# ADR-001: Choose Queued or Synchronous Document Processing

## Context
The document-processing endpoint sometimes exceeds its HTTP request timeout. The client may time out while processing continues, making retries and failure detection difficult.

## Options

**Synchronous**
- Simple request-response flow.
- Suitable for short operations.
- Long-running requests can time out, and retries may duplicate work.

**Queued**
- Returns HTTP 202 Accepted with a job ID.
- Processes documents in a background worker.
- Requires additional infrastructure, status tracking, retries, and recovery.

## Requirements
Review R1–R8 in `requirements.md` against the proposed design and available evidence.

## Evidence
- Requirements: `requirements.md`
- API contract: `api-contract.md`
- Synthetic traces: `evidence/synthetic-traces.csv`
- Architecture diagram: Add the Miro board link after creating the diagram.

## Verification
- [ ] R1–R8 reviewed against the proposed design and available evidence.
- [ ] Unverified behavior identified as unresolved.

## Remaining Risks
Production latency, queue reliability, duplicate processing, worker recovery, and retry behavior require further validation.

The six synthetic traces support architecture reasoning but do not prove production reliability.
