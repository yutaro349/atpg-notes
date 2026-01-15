```mermaid
flowchart TD
  A((Start)) --> B[Input cube v<br/>Netlist FFs]
  B --> C[Make tuples<br/>v R1 R2]
  C --> D[Classify X type]
  D --> E{No X left}
  E -- Yes --> Z((Done v*))

  E -- No --> F[Count ECT PCT<br/>for C1 C2]
  F --> G[Compute TECTA<br/>for C1 C2]
  G --> H{Pick target<br/>max TECTA}
  H -- C1 --> I[Target C1]
  H -- C2 --> J[Target C2]
  I --> K
  J --> K

  K[Pick tuple<br/>helps target]
  K --> L{Assignment OK}
  L -- Yes --> M[Assign X in v]
  L -- No --> N[Justify via logic<br/>use JE]

  M --> O[Sim update]
  N --> O

  O --> P{Success}
  P -- Yes --> D
  P -- No --> Q[Try next tuple]
  Q --> D
 ```
