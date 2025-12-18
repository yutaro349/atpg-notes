```mermaid
flowchart TD
  Q[Initialize queue with changed nodes] --> LOOP{Queue empty}
  LOOP -- No --> POP[Pop one node n]
  POP --> FWD[Forward evaluate fanout gates<br/>apply branch injection then gate eval then stem injection]
  FWD --> CHG{Any value changed}
  CHG -- Yes --> ENQ[Push affected fanouts into queue]
  CHG -- No --> BWD
  ENQ --> BWD[Backward implication<br/>limited rules for BUFF NOT AND OR]
  BWD --> LOOP
  LOOP -- Yes --> END[Finish implication]
