flowchart LR
  ZK[(zookeeper)]
  Kafka[(kafka)]
  Setup[kafka-setup - creates topics]
  KafkaUI[kafka-ui]

  Interface[interface - Streamlit]
  Fraud[fraud_detector - ML scoring service]

  Kafka --- ZK
  Setup -->|creates: transactions, scoring| Kafka
  KafkaUI -->|browse topics| Kafka

  Interface -->|produce: transactions| Kafka
  Kafka -->|consume: transactions| Fraud
  Fraud -->|produce: scoring| Kafka

  subgraph FraudInternal[fraud_detector internal components]
    Consumer[Kafka consumer]
    Preproc[Preprocessing]
    Inference[Model inference]
    Producer[Kafka producer]
    Consumer --> Preproc --> Inference --> Producer
  end

  Fraud --> Consumer
  Producer --> Fraud
