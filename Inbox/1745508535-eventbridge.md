---
id: 1745508535-eventbridge
aliases:
  - EventBridge
tags: []
---

# EventBridge

EventBridge acts as AWS event bus, enabling services to communicate with one another through the EventBridge service. It decouples our services and takes care or routing and filtering the events to the designated service.

Components:
- EventBus: Collects and forwards the event to the necessary locations
- Rules: specify rules for filtering and targeting services.
- Event Source: The source that send the event to the EventBus

We can build EventBridge Pipes that can also enrich the events with data.

The Scheduler provides us with retry policies and patterns when to trigger certain EventBridge events that show up.


Features:
- Low Code Integration: Send events to different APIs.
- Event Replay: helps for debugging failed events that gives us insights of failed events.
- Schema Registry: Data Schema that define the shape of the events.
- Automatic Retries


