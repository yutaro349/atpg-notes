```mermaid
flowchart TD
  subgraph Inject[Fault injection in simulate_and_imply]
    B1[Branch fault injection] --> B2[inject at gate input pin<br/>inject_branch_at_input]
    S1[Stem fault injection] --> S2[inject at gate output<br/>inject_stem_output]
  end

  B2 --> R1[result becomes 0 1 D or Db]
  S2 --> R2[result becomes 0 1 D or Db]
