# Day 23 — Distributed Saga Order Orchestration Platform

Java 17 + Spring Boot 3.3.5 project demonstrating the **Saga orchestration pattern** and compensating transactions.

## Services
- Order Service :8081 — order lifecycle
- Payment Service :8082 — authorize/refund
- Inventory Service :8083 — reserve/release
- Saga Orchestrator :8084 — coordinates the workflow and compensation

## Run
```bash
docker compose up --build
```

## Success
```bash
curl -X POST http://localhost:8084/api/saga/checkout -H "Content-Type: application/json" -d '{"sku":"LAPTOP-001","quantity":1,"amount":49999}'
```

## Failure / compensation
```bash
curl -X POST http://localhost:8084/api/saga/checkout -H "Content-Type: application/json" -d '{"sku":"LAPTOP-001","quantity":1,"amount":49999,"forceFail":true}'
```

When a step fails, the orchestrator executes compensating actions and returns `COMPENSATED`.

## GitHub
```bash
git init && git add . && git commit -m "Day 23 distributed saga platform"
git branch -M main
git remote add origin https://github.com/Vermaaditya3030/distributed-saga-day23.git
git push -u origin main
```

## Production roadmap
Kafka events, PostgreSQL persistence, transactional outbox, idempotency, retries/circuit breakers, tracing, JWT, durable saga state, Kubernetes.
