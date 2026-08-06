# Architecture — FeatureBase

## High-Level Design (HLD)
FeatureBase computes and caches features in Redis so models get consistent, low-latency feature values at inference time, with the same definitions used for training and serving.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#ffffff','lineColor':'#2563eb','mainBkg':'#ffffff'}}}%%
graph LR
    A([Event])
    B([Feature Compute])
    C([Redis Store])
    D([Serve to Model])
    A --> B
    B --> C
    C --> D
    style A fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style B fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style C fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style D fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
```

**Flow:** Event → Feature Compute → Redis Store → Serve to Model

## Low-Level Design (LLD)
- **Components:** `Redis`, `Node.js`
- **Interfaces / contracts:** to be finalized during implementation.
- **Data model:** to be defined per component.

## Decision Log
- **Why this stack:** **Redis** — in-memory store / cache / queue; **Node.js** — application runtime / service layer.
- ** constraint:** run logic/state/UI locally; offload heavy reasoning to cloud APIs; target modest hardware.

## Concept Deep Dive
Train/serve consistency — making sure the feature a model sees online matches how it was trained.
