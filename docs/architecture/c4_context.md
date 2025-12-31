flowchart LR
  User[User / Analyst]
  Interface[interface - Streamlit Web UI]
  Kafka[(Kafka)]
  System[Fraud Detection System]

  User -->|uses UI| Interface
  Interface -->|produces to topic: transactions| Kafka
  Kafka -->|delivers transactions (consume)| System
  System -->|publishes to topic: scoring| Kafka
