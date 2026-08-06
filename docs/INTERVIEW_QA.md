# Interview Q&A — FeatureBase

### "Tell me about this project."
FeatureBase is real-time feature store serving low-latency features to models online. FeatureBase computes and caches features in Redis so models get consistent, low-latency feature values at inference time, with the same definitions used for training and serving.

### "What was the hardest part?"
Train/serve consistency — making sure the feature a model sees online matches how it was trained.

### "Why did you choose this stack?"
- **Redis** — in-memory store / cache / queue.
- **Node.js** — application runtime / service layer.

### "How does it fit the rest of your portfolio?"
It follows my "" model — local logic/state/UI, cloud reasoning where it earns its cost — and shares the documentation and deployment conventions used across all my projects.
