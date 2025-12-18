```mermaid
flowchart TD
  S[Start: init State or TDFState] --> SIM0[Initial implication<br/>simulate_and_imply]
  SIM0 --> OK{Success at any PO<br/>D or Db observed}
  OK -- Yes --> OUT[Return test vector]
  OK -- No --> OBJ[Compute objective<br/>getobjective or getobjective_tdf]
  OBJ -->|No objective| FAIL[Return no test]

  OBJ --> BT[Backtrace objective to a PI]
  BT --> TRY1[Assign PI with target value<br/>record change and imply]
  TRY1 --> REC1[Recurse podem_rec]
  REC1 --> OK1{Success}
  OK1 -- Yes --> OUT
  OK1 -- No --> UNDO1[Undo trail]

  UNDO1 --> TRY2[Assign PI with opposite value<br/>record change and imply]
  TRY2 --> REC2[Recurse podem_rec]
  REC2 --> OK2{Success}
  OK2 -- Yes --> OUT
  OK2 -- No --> FAIL
