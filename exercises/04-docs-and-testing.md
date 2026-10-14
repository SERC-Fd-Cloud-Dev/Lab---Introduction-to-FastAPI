# 04 — Inspect the contract and write a health test

**17 minutes · supported · individual work**

Starting point: working routes. The guided router refactor is the expected
class stage, but the test can also run while your routes remain in one file.

## Documentation audit — about 5 minutes

Open `/docs`, `/openapi.json`, and your earlier `design/openapi.yaml` contract.
In the learning log, record evidence for the API title/version, implemented
paths, methods, responses and schemas. Record one match and one gap with your
design. If a route exists only in your design, explain why it is absent from
the generated document.

A response can contain `id`, `name` and `location` while its generated schema
remains broad. Without explicit models/appropriate return-type declarations,
observed data does not by itself become a precise field-level contract.
You do not need to introduce Pydantic response models in this exercise.

## Write your own test — about 12 minutes

Create `tests/test_health.py`. Use `TestClient` from `fastapi.testclient` and
import `app` from `app.main`. Write a test function named
`test_health_returns_ok`. Use a TestClient context manager, request `/health`,
and assert both HTTP 200 and exact JSON equality with `{"status": "ok"}`.

Refer to the tutor's test pattern or the official testing reference in
`docs/concepts.md`. You write the test; a completed equipment health test is
deliberately not supplied in the starter.

Run from the exercise folder in a second terminal with the same environment:

```bash
python -m pytest -q
```

Stop Uvicorn and rerun the test once. Explain why TestClient does not need
a separately running server. It sends a request through the app in process.

Temporarily change your expected body to `{"status": "ready"}`. Predict the
result, run the test, and interpret the assertion failure. Restore `ok` and
run successfully before committing. Keep the app's response unchanged.

## Evidence and limits

Record the passing result, deliberate failure, restored result, and one thing
the test does not prove. A passing health test is evidence for this endpoint's
behaviour; it does not establish database readiness, deployment or full contract
compliance. Commit the test and learning-log update, then push.

No tests collected is not a pass. Do not use `pass`, unconditional assertions
or a skip marker as a substitute for a real route check. If a test fails,
inspect the actual response and the assertion before changing expectations.
