```mermaid
flowchart TD
  A([Start: DC-LCP X-filling]) --> B[Input: Test cube v (0/1/X)\n+ Circuit netlist + FF list]
  B --> C[Build 3-bit-tuples for each FF:\n< v:FF , R1:FF , R2:FF >\n(using current assignments + logic simulation)]
  C --> D[Classify each tuple into X-Type (Type1..8)]
  D --> E{All tuples are Type-1?\n(no X remains)}
  E -- Yes --> Z([Output: Fully specified test vector v*]) 

  E -- No --> F[Compute ECT/PCT for C1 and C2\n(From tuple states: definite vs possible transitions)]
  F --> G[Compute TECTA1, TECTA2:\nTECTAi = #ECTi + 0.5 * #PCTi]
  G --> H{Target capture?\n(choose larger TECTA)}
  H -- C1 --> I[Set target = C1]
  H -- C2 --> J[Set target = C2]
  I --> K
  J --> K

  K[Select candidate tuples that can reduce\ntransition on target capture\n(based on Table-1 target-capture rules)] --> L{Any candidate solvable by\nAssignment only?\n(v:FF has X and setting it suffices)}
  L -- Yes --> M[Pick one (heuristic: best expected reduction,\noptional: tie-break by fanout/weight)]
  L -- No --> N[Pick tuple for Justification\nusing JE (Justification Easiness):\n- Prefer tuples needing 1 X-line justification\n- Else maximize sum of JE for required lines]

  M --> O[X-filling Operation]
  N --> O

  O --> P{Solve by Assignment?}
  P -- Yes --> Q[Assign v:FF X -> 0/1\n(choose value that removes target transition)]
  P -- No --> R[Justification procedure:\nTry best assignment pattern first\n(e.g., <1,X,X> try 11 -> 10 -> 00 -> 01)\nBacktrack/Failover if conflict]
  
  Q --> S[Logic simulation update:\npropagate new assignments\nupdate <v,R1,R2> values]
  R --> S

  S --> T{Justification succeeded?}
  T -- Yes --> C
  T -- No --> U[Mark this tuple/attempt as failed\nChoose next best pattern or next tuple\n(optional: limit retries)]
  U --> C
 ```
