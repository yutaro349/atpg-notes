```mermaid
flowchart TD
  subgraph FaultInjection[故障注入ポイント]
    A1[branch故障] --> B1["simulate_and_imply 内\nゲート入力(pin)に注入\ninject_branch_at_input()"]
    A2[stem故障] --> B2["simulate_and_imply 内\nゲート出力に注入\ninject_stem_output()"]
  end

  B1 --> C1["(good_value) を\nD/Db/0/1 に変換"]
  B2 --> C2["(gate out) を\nD/Db/0/1 に変換"]
