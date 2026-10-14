# Lab - Introduction to FastAPI — Equipment Inventory exercises

Build a small API, organise it into modules, and verify its HTTP interface.
This repository contains the instructions, starter application, static data,
and your editable learning record. Complete the coding and written work here.

Work in your own repository copy. Each student implements and explains their
own code; use a partner for checks and feedback. The campus equipment inventory
is a teaching project that can grow in later lessons.

## What you will practise

- Implement simple FastAPI routes and JSON responses, including a health route.
- Refactor a working resource route with `APIRouter` under guidance.
- Explain the purpose of dependency injection without implementing it.
- Compare generated OpenAPI with the intended interface and write a route test.

You should already know Python functions, dictionaries, lists and modules;
HTTP methods/status codes; and the Git/environment workflow from earlier lessons.

## Start here

1. Follow [setup and repository access](docs/setup.md) before the coding session.
2. Read the [expected interface](design/expected-interface.md).
3. Complete the exercises below in order. Edit [your learning log](evidence/learning-log.md)
   as you work and commit meaningful increments.

| Stage | Time | Support | Work and evidence |
|---|---|---|---|
| [01 — First routes](exercises/01-first-routes.md) | 20 min | Guided | Two routes in `app/main.py`; observed status, headers and bodies |
| [02 — Router refactor](exercises/02-router-refactor.md) | 15 min, including demonstration | Guided | Same interface after moving the resource route into a router |
| [03 — Dependency recognition](exercises/03-dependency-recognition.md) | 5 min | Code reading | Explain who supplies a dependency; no application changes |
| [04 — Documentation and first test](exercises/04-docs-and-testing.md) | 17 min | Supported | Contract comparison, student-written health test, deliberate failed assertion |
| [05 — Homework primer](exercises/05-homework-primer.md) | 3 min | Worked example | Path parameters and HTTP errors using a different resource |
| [Peer review and exit](exercises/06-peer-review.md) | 10 min | Review | Feedback and individual explanations |
| [Homework — Detail endpoint](exercises/07-homework.md) | About 60 min | Independent with hints | Static-data detail route, successful/missing-item tests, commit and explanation |
| [Optional — Limit parameter](exercises/08-optional-limit.md) | Extra time | Challenge | Restrict list results without breaking existing behaviour |
| [Homework review](exercises/09-homework-review.md) | 60 min review session | Feedback and improvement | Retrieval, peer checks and a committed correction |

The initial tutor demonstration of Shuttle Stops precedes Exercise 01.
Preparation is separate from these practical timings. Catch-up study may take longer.

## Starting state

`app/main.py` imports FastAPI and creates an application instance. It contains
**no equipment or health route implementations**. The three data records are
provided in `data/equipment.json`. You create the router modules in Exercise 02
and the tests in Exercise 04/homework. The starter has no completed route tests.

The server can start immediately: `/docs` and `/openapi.json` exist, but requests
to `/health`, `/equipment`, and `/` initially return 404. This is expected.
Before you write a test, pytest reports no tests collected and exits with code 5;
that is a starting state, not evidence of a passing test.

The exercises use local static data. Database storage, full validation models,
authentication and substantial dependency-injection implementation come later.

## Files you will work on

| File or directory | Your work |
|---|---|
| `app/main.py` | First routes, then router registration |
| `app/routers/` | Create during the guided refactor |
| `tests/` | Write your own tests; see its README |
| `design/openapi.yaml` | Bring your design contract from the REST/OpenAPI sub-lesson |
| `evidence/learning-log.md` | Record observations, explanations and review feedback |

The supplied data and dependency pins provide a common starting point. Keep them
stable during the core exercise. `requests.http` and the Postman collection are
optional request aids; no editor extension is required to complete the work.

## Completion and recovery

- [ ] I can explain how a route maps an HTTP request to a Python function.
- [ ] Both single-file routes work and still work after the guided refactor.
- [ ] I can explain router creation and registration as separate steps.
- [ ] I recorded a design/generated-contract match and a gap.
- [ ] My own health test passes, and a deliberately wrong body expectation fails.
- [ ] My learning log and meaningful commits record the work.

If behind, complete the two routes, inspect their generated documentation, and
write the health test first. The test works with a single-file application too.
Finish the router refactor with support during review. Dependency injection is
a recognition task, not a required coding checkpoint. Use the
[troubleshooting guide](docs/troubleshooting.md) to diagnose a specific failure.

Stop the server with Ctrl+C after work. If you activated the environment, use
`deactivate` when finished. Bring your repository and learning log to review.

Essential explanations and official sources are in [concepts and references](docs/concepts.md).
