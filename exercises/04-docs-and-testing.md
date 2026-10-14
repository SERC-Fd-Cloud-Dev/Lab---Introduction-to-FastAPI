# 04 — Inspect the contract and write a health test

**17 minutes · supported practice, ending with an independent check**

Starting point: the health and equipment routes work. The router refactor is
the expected class stage, but the test can also run while the routes remain in
one file. No test file is supplied: you will create a real test yourself.

## Read the generated interface — about 5 minutes

Open `/docs`, `/openapi.json` and your earlier `design/openapi.yaml`. FastAPI
generates OpenAPI from operations registered on the running application;
`/docs` presents an interactive view of that document. It describes the
implemented interface, not every route that may be planned in your design.

Compare the title/version, implemented paths and methods, responses and
available schemas. Record one match and one gap in the learning log, and explain
why a route that is only in your design is absent from generated OpenAPI. A
response may contain `id`, `name` and `location` while the generated response
schema remains broad: observed dictionary fields do not automatically provide
a precise field-level schema. Pydantic response models are not required here.

## Pytest and TestClient — about 2 minutes

`pytest` discovers test files named `test_*.py` and test functions named
`test_*`. It runs them and reports whether their assertions passed or failed.
Run it from the exercise folder with `python -m pytest -q`; using `python -m`
helps ensure pytest runs with the selected Python environment.

FastAPI's `TestClient` sends requests to the app inside the test process. It
lets a test check real HTTP response status and JSON without starting Uvicorn
or making a network request. Import the supplied `app` from `app.main`, then
create the client with `TestClient(app)` (a context manager is recommended).
The request should still pass through FastAPI's routing and response handling.

Before adding a test, pytest collects none and exits with code 5. That means
there was no test to run; it is neither a pass nor a failure of the health
route. A test with no meaningful assertions is not evidence either.

## Build a real test — about 10 minutes

Follow these steps to create `tests/test_health.py`; write the code yourself:

1. Import `TestClient` from `fastapi.testclient` and import `app` from
   `app.main`. These are the test client and the application under test.
2. Define a test function named `test_health_returns_ok`. The `test_` prefix
   lets pytest discover it.
3. Within the test, open a `TestClient` context for the app and request
   `/health`. Keep the response so you can inspect its properties.
4. Add two assertions: one that the status is 200, and one that the decoded
   JSON equals the exact health body in `design/expected-interface.md`.
   Assertions compare expected behaviour with actual behaviour; do not replace
   them with `pass`, skips or unconditional assertions.
5. Run `python -m pytest -q` from the exercise folder. Read the failure output
   if either assertion fails; compare the response with the contract before
   changing code or expectations.

Consult the tutor's basic test walkthrough or the official testing reference in
`docs/concepts.md` if you need help with Python syntax. The test-writing task,
not a completed health test, is the scaffold provided here.

## Check independently and record evidence

Stop Uvicorn with Ctrl+C and run the test again. It should still pass because
TestClient calls the app in process. Record this result in
`evidence/learning-log.md`.

Now predict what happens if the expected JSON is temporarily changed to
`{"status": "ready"}`. Make only that test change, rerun pytest, and inspect
the assertion failure. Restore the contract's expected value and rerun until
the test passes. Do not change the app response to make the deliberate failure
go away.

Record the correct run, deliberate failure, restored run and one thing the
health test does not prove. A passing test is evidence for this endpoint's
behaviour, not database readiness, deployment or full contract compliance.
Commit the real test and learning-log evidence, then push.
