# Real-Time Fraud Detection System

Сервис детекции мошеннических транзакций в реальном времени,
реализованный в рамках курса по MLOps (МТС ШАД 2025).
Система использует ML-модель для скоринга транзакций и Kafka
для потоковой обработки данных.

---

## Архитектура

Архитектура системы задокументирована с использованием методологии **C4**
и представлена на двух уровнях детализации:

- **C4 Level 1 — Контекст системы**  
  [`docs/architecture/c4_context.md`](docs/architecture/c4_context.md)

- **C4 Level 3 — Компоненты системы**  
  [`docs/architecture/c4_components.md`](docs/architecture/c4_components.md)

- **Пояснительная записка по архитектуре**  
  [`docs/architecture/architecture.md`](docs/architecture/architecture.md)

Диаграммы отражают взаимодействие пользователя, Kafka и сервиса детекции фрода,
а также внутреннюю структуру основного сервиса скоринга.

---

## Основные компоненты системы

- **interface** — Streamlit-приложение для симуляции потоковых транзакций
  и отправки сообщений в Kafka.
- **fraud_detector** — сервис скоринга транзакций с использованием
  предобученной модели CatBoost.
- **Kafka infrastructure** — брокер сообщений (Kafka + Zookeeper),
  используемый для передачи транзакций и результатов скоринга.

---

## Технологический стек
- Python
- Apache Kafka
- Docker / Docker Compose
- Streamlit
- CatBoost

---

## Запуск проекта

```bash
docker compose up --build

После запуска:

Streamlit UI: http://localhost:8501

Kafka UI: http://localhost:8080
