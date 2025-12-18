```mermaid
flowchart TB
  subgraph STR["TDF STR (0 -> 1) modeling"]
    A["Constraint: t0_Y = 0 (must launch 0)"]
    B["Fault injection: t1_Y behaves like SA0 (stuck at 0)"]
    A --> B
  end

  subgraph STF["TDF STF (1 -> 0) modeling"]
    C["Constraint: t0_Y = 1 (must launch 1)"]
    D["Fault injection: t1_Y behaves like SA1 (stuck at 1)"]
    C --> D
  end
