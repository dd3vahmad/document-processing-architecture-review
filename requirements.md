# Requirements

## Functional requirements

- R1: The API must accept a document-processing request and identify the submitted document.
- R2: The client must receive a clear outcome or acknowledgement.
- R3: The client must be able to determine whether processing is pending, completed, or failed.
- R4: Repeating a request after a timeout must not unintentionally process the same logical request twice.
- R5: Processing failures must have a defined recovery or terminal-failure path.

## Operational requirements

- R6: The request must remain useful even when processing exceeds the HTTP request timeout.
- R7: Failures must be observable through job status and operational logs.
- R8: The architecture must account for worker crashes, retries, and requests that cannot be processed successfully.

## Decision criteria

Compare both approaches on:
- Client response behavior and timeout handling.
- Failure recovery and duplicate prevention.
- Implementation and operational complexity.
- Workload spikes and independent scaling.

## Constraints and open questions

- The actual request timeout has not yet been established.
- No production latency distribution or throughput data is available.
- Queue durability, processing deadlines, and retention requirements need confirmation.
- The review must distinguish demonstrated evidence from assumptions.
