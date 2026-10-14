# 01 — Implement your first routes

**20 minutes · guided · individual implementation**

Practise mapping a method/path to a Python function, then observing the HTTP
response. Begin after the tutor's simple Shuttle Stops demonstration and setup.

## Work through it

1. Open `app/main.py`. Explain the import, application instance, title and version
   already supplied. There are no route functions yet.
2. Define a function for `GET /health`, using an application route decorator.
   Return the dictionary specified in `design/expected-interface.md`.
3. Define a static Python list with the three supplied equipment records. Use
   `data/equipment.json` as the reference; no JSON file-loading code is required.
4. Define `GET /equipment` to return that list. Keep the data and both routes in
   `main.py`. Do not add `APIRouter`, `Depends` or additional application layers yet.
5. Before running, complete the predictions in `evidence/learning-log.md`:
   which function will run, what body will return, and what will happen at `/`?
6. From the exercise folder start `python -m uvicorn app.main:app --reload`.
7. Request `/health` and `/equipment` through Postman or Swagger UI. Record
   the actual status, `Content-Type` and JSON. The supplied Postman collection
   and `requests.http` are optional shortcuts.
8. Open `/docs`, find both operations, then use **Try it out → Execute** on one.
   Explain how a Python return value becomes an HTTP JSON response.

## Check and save

Both requests return 200 with the exact specified bodies. The response media
type is JSON. The equipment array has all three records. A 404 at `/` is fine.
Compare your predictions with the observed results and explain any difference.

Update the Exercise 01 section of the learning log, then commit the working routes
and evidence, for example **Add initial health and equipment routes**. Push to
your own repository using the setup guide's branch workflow.

If stuck, check that the decorators use the `app` instance and a leading `/`.
A returned JSON-like string is not the same as returning a list/dictionary.
Use `docs/troubleshooting.md` for environment/import problems.

Continue only once both routes work. The next exercise changes organisation
while preserving this observable interface.
