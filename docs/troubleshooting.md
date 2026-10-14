# Troubleshooting and catch-up

| Symptom | Check and next action |
|---|---|
| `Could not import module app.main` | Run from the exercise folder containing `app/`; check module names and `__init__.py` |
| Module `fastapi`, `pytest` or `httpx` missing | Select/activate the exercise environment and install with that Python's pip |
| Health/list 404 in the starting app | Expected before Exercise 01; write the routes |
| Health/list 404 after refactor | Check saved files, router import, `include_router`, prefix and suffix |
| Duplicate or unexpected equipment paths | Remove the old application route; avoid repeating the prefix |
| Address already in use | Stop the previous server with Ctrl+C; if using another port, update every request URL |
| Swagger UI is blank | Its external assets may be blocked; use `/openapi.json` and Postman/direct requests |
| No tests collected | Create a `test_*.py` file with a `test_` function and real assertions; this is not a pass |
| Test fails after changing expectation | Read the actual status/body; restore the correct contract after the deliberate-failure exercise |
| Unknown ID test passes before detail implementation | A missing route also gives 404; check a successful ID and the exact missing-item body |
| Git cannot find a repository | Work within your clone; do not create nested history in the exercise directory |

Diagnose one failure at a time: reproduce it, note what you expected, inspect
the actual evidence, make one change, and rerun the same check.

## Minimum catch-up route

Read `docs/concepts.md`, finish the two single-file routes, inspect their docs,
and write/run the health test. This establishes the essential request/response
pattern. Complete the router refactor with support during review; no dependency
injection implementation is needed. Read the path/error primer before homework.

Retain your failed attempt and short diagnostic note if you need help. Stop the
server with Ctrl+C at the end. No cloud resources are created by this exercise.
