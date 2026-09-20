# Reasoning guide — agents

First prove that a deterministic workflow cannot express the required uncertainty. Agents need
bounded loops, typed tools, authorization, durable state, idempotency, checkpoints, and human
approval. Evaluate recovery and tool behavior, not only final success. Frameworks come after these
contracts are understood.
