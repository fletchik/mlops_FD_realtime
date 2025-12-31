# C4 Level 3 — Components

```mermaid
flowchart LR
  ZK[Zookeeper]
  Kafka[Kafka]
  Setup[Kafka setup]
  KafkaUI[Kafka UI]

  Interface[Interface Streamlit]
  Fraud[Fraud detector service]

  Kafka --- ZK
  Setup -->|creates topics| Kafka
  KafkaUI -->|views topics| Kafka

  Interface -->|produces transactions| Kafka
  Kafka -->|sends transactions| Fraud
  Fraud -->|publishes scores| Kafka

  subgraph FraudInternal[Fraud detector internal components]
    Consumer[Kafka consumer]
    Preprocessing[Preprocessing]
    Inference[Model inference]
    Producer[Kafka producer]

    Consumer --> Preprocessing
    Preprocessing --> Inference
    Inference --> Producer
  end

  Fraud --> Consumer
  Producer --> Fraud
