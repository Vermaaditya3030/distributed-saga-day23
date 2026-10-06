# Architecture

Client → Saga Orchestrator → Order / Inventory / Payment.

Forward flow: create order → reserve inventory → authorize payment → complete order.

Failure flow: release inventory → refund payment when authorized → cancel order.

This is a learning implementation. Production systems should persist saga state and use idempotent commands plus an outbox/event bus.
