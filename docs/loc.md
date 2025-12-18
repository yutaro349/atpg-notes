```mermaid
flowchart LR
  subgraph T0[Time 0 signals]
    PI0[t0 primary inputs]
    Q0[q0 FF outputs treated as PI]
    C0[t0 combinational logic]
    D0[t0 FF D inputs]
  end

  subgraph FFAbs[FF abstraction in 2TF network]
    Q1[q1 equals BUFF of t0 D<br/>launch state into time 1]
    Q2[q2 equals BUFF of t1 D<br/>observe next state]
  end

  subgraph T1[Time 1 signals]
    PI1[t1 primary inputs equals BUFF of t0 PI]
    C1[t1 combinational logic]
    PO1[t1 primary outputs]
    D1[t1 FF D inputs]
  end

  PI0 --> C0 --> D0
  Q0 --> C0

  D0 --> Q1 --> C1
  PI0 --> PI1 --> C1 --> PO1
  C1 --> D1 --> Q2
