# 06 — Peer review and individual exit check

**5 minutes peer review + 5 minutes individual reflection**

Swap reviewer/operator roles halfway through the peer check. Each student
operates and explains their own repository; record feedback in the learning log.

- Request `/health` and `/equipment`, then inspect status and JSON.
- Locate the router and its registration; confirm the old route was removed.
- Run the health test and explain both assertions.
- Give one specific strength and one actionable improvement.

If working alone, apply the same criteria and record one change to make.

Answer the individual exit prompts in `evidence/learning-log.md`: justify one
REST design choice; explain the role of an IDL contract; explain what a router
changes; and identify who calls a dependency provider. Use concrete observations.
Commit the log and push your branch to your own repository.

**Self-check:** a resource-oriented GET path, a machine-readable interface
description, grouped route definitions with the same HTTP behaviour, and
FastAPI calling a provider are the core ideas. Name the relevant evidence
in your own application rather than merely repeating those phrases.
