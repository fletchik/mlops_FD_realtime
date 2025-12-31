# C4 Level 1 — System Context

```mermaid
flowchart LR
  User[User Analyst]
  Interface[Interface Streamlit UI]
  Kafka[Kafka]
  System[Fraud Detection System]

  User -->|uses UI| Interface
  Interface -->|produces transactions| Kafka
  Kafka -->|delivers transactions| System
  System -->|publishes scores| Kafka
