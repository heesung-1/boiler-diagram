# Boiler Recommendation Logic

```mermaid
flowchart TD
  S([Start])
  S --> Q5{Q5. Drain present?}
  Q5 -- Yes --> T1[Type = Condensing]
  Q5 -- No/Unknown --> T2[Type = Non-condensing]

  T1 --> Q2
  T2 --> Q2
  Q2 --> A1[<=20]
  Q2 --> A2[21-25]
  Q2 --> A3[26-30]
  Q2 --> A4[31-35]
  Q2 --> A5[36-40]
  Q2 --> A6[>40]

  A1 --> Q4{Q4. Bathrooms?}
  A2 --> Q4
  A3 --> Q4
  A4 --> Q4
  A5 --> Q4
  A6 --> Q4

  Q4 -- ">=2" --> B2[Use LUT table (2+ bathrooms)]
  Q4 -- "1" --> B1[Use LUT table (1 bathroom)]

  B1 --> C[Lookup capacity from table]
  B2 --> C

  C --> Q3{Q3. Discomfort tags}
  Q3 --> SCORE[Score models by tag match]

  SCORE --> RINN[Pick 1 model in Rinnai]
  SCORE --> KIT[Pick 1 model in Kiturami]
  SCORE --> KYU[Pick 1 model in Kyungdong]

  RINN --> OUT1[Output #1: Rinnai (top)]
  KIT --> OUT2[Output #2: Kiturami]
  KYU --> OUT3[Output #3: Kyungdong]



