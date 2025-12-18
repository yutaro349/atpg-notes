```mermaid
graph TD;
  A[Start] --> B[PODEM/TDF build 2TF network];
  B --> C{Objective?};
  C -->|excite| D[D-frontier propagation];
  C -->|not excite| E[Backtrace to PI];
  D --> F[Imply/Simulate];
  E --> F;
  F --> G{PO has D/Db ?};
  G -->|yes| H[DETECTED];
  G -->|no| I[Backtrack];
  I --> C;
