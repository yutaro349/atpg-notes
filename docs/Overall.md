```mermaid
flowchart TD
  A[CLI main] --> B{Is --tdf enabled}

  B -- No --> C[parse_bench_seq: read PI PO gates DFF]
  C --> D[podem: single timeframe stuck-at]
  D --> Z[Print test vector]

  B -- Yes --> E[parse_bench_seq: nodes PIs POs ff_pairs prim_PIs]
  E --> F[build_broadside_two_timeframe: build 2TF network nodes2]
  F --> G[_resolve_tdf_lines: map fault line to t0/t1 or q0/q1]
  G --> H[podem_tdf: run PODEM with TDFState]
  H --> I[Back-map to original PIs and FF Qs]
  I --> Z

