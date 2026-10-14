# Essential concepts and references

A FastAPI application instance holds the HTTP interface. A route decorator
associates a method/path with a function. For these exercises, returning a
Python dictionary/list produces a JSON response. Uvicorn serves the app over HTTP.

`APIRouter` groups related operations. Creating one defines the group; including
it in the application registers those operations. Moving a route should preserve
its intended method, path and behaviour. This is organisation, not a new service.

OpenAPI describes the interface in a machine-readable form. FastAPI generates
a document from the implementation, available at `/openapi.json`; `/docs` uses
it for interactive exploration. Compare that generated document with the design
you intended. A generated document is not proof that the whole design was implemented.

TestClient exercises the app in process. Assert the response status and JSON
body for the behaviour you claim. A route test and a live server request provide
different evidence; neither alone establishes all aspects of service reliability.

Dependency injection lets FastAPI supply a provider's result to code that needs
it. Its purpose is introduced here; students practise implementation when later
lessons need database sessions or authentication.

| Official source | Use |
|---|---|
| [FastAPI — First Steps](https://fastapi.tiangolo.com/tutorial/first-steps/) | Application instance, decorators, generated docs |
| [FastAPI — Bigger Applications](https://fastapi.tiangolo.com/tutorial/bigger-applications/) | Router creation and registration |
| [FastAPI — Dependencies](https://fastapi.tiangolo.com/tutorial/dependencies/) | Dependency-injection concept |
| [FastAPI — Testing](https://fastapi.tiangolo.com/tutorial/testing/) | TestClient and pytest pattern |
| [FastAPI — Path Parameters](https://fastapi.tiangolo.com/tutorial/path-params/) | Parameter names and integer annotations |
| [FastAPI — Handling Errors](https://fastapi.tiangolo.com/tutorial/handling-errors/) | HTTPException and HTTP error responses |
| [Python 3.14 — venv](https://docs.python.org/3.14/library/venv.html) | Environment creation and terminal-specific activation |
| [GitHub — Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) | Personal copy of the class starter |

Use the pinned package manifest supplied with the exercise. Online documentation
may show newer tools or installation choices; do not change the class environment
just to match a documentation example. Ask for support if its behaviour differs.
