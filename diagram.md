```mermaid
flowchart TD
  S([Start])
  S --> Q5{Q5 drain present}
  Q5 -- Yes --> T1[Type Condensing]
  Q5 -- No or Unknown --> T2[Type Noncondensing]

  T1 --> Q2[Q2 floor area pyeong]
  T2 --> Q2
  Q2 --> A1[<=20 pyeong]
  Q2 --> A2[21-25 pyeong]
  Q2 --> A3[26-30 pyeong]
  Q2 --> A4[31-35 pyeong]
  Q2 --> A5[36-40 pyeong]
  Q2 --> A6[>40 pyeong]

  A1 --> Q4{Q4 bathrooms}
  A2 --> Q4
  A3 --> Q4
  A4 --> Q4
  A5 --> Q4
  A6 --> Q4

  Q4 -- "2 or more" --> B2[Use LUT 2plus baths]
  Q4 -- "1" --> B1[Use LUT 1 bath]

  B1 --> C[Lookup capacity table]
  B2 --> C

  C --> Q3{Q3 discomfort tags}
  Q3 --> SCORE[Score models by tag match]

  SCORE --> RINN[Pick 1 in Rinnai]
  SCORE --> KIT[Pick 1 in Kiturami]
  SCORE --> KYU[Pick 1 in Kyungdong]

  RINN --> OUT1[Output Rinnai top]
  KIT --> OUT2[Output Kiturami]
  KYU --> OUT3[Output Kyungdong]









