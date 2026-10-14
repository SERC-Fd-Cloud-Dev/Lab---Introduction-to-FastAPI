# 01 — Implement your first routes

**20 minutes · guided start, then individual implementation**

Practise mapping an HTTP request to a Python function and checking the response.
Begin after the tutor's different Shuttle Stops demonstration and setup.

## FastAPI in brief

FastAPI is a Python framework for describing HTTP interfaces and serving them
as an application. In `app/main.py`, `app` is the application instance. A
decorator such as `@app.get("/some-path")` tells FastAPI to handle GET requests
for that path with the function immediately below it. The function is the
*route handler*. FastAPI calls it when a matching request arrives.

For this exercise, a route handler returns a Python dictionary or list. FastAPI
encodes that value as a JSON response and supplies an HTTP status and headers.
Uvicorn is the server that accepts network requests and serves the application.
The application, route handler and server have related but distinct jobs.

Here is a small example for a different path. The decorator is attached to the
function directly below it, and the function returns ordinary Python data:

```python
@app.get("/hello")
def say_hello():
    return {"message": "Hello"}
```

Read it as: for a GET request to `/hello`, FastAPI calls `say_hello`; the
returned dictionary becomes a JSON response. This is a syntax example only:
do not add `/hello` to your app. In the steps below, use the interface contract
to choose the route path, handler name and response for each Equipment operation.

## Guided start — about 5 minutes

1. Open `app/main.py`. Identify the FastAPI import and the supplied `app`
   instance. The string `app.main:app` used to start Uvicorn means: import the
   `app` module inside the `app.main` Python module.
2. Find `design/expected-interface.md`. Read the health route's method, path,
   status and response. Explain what each part describes before writing code.
3. Predict which function should handle `GET /health` and what a client should
   receive. Record the prediction in `evidence/learning-log.md`.

## Build and inspect — about 15 minutes

4. Write a handler in `app/main.py` for the health operation. Attach it to the
   supplied application with a GET route decorator and return the required
   dictionary. Keep the response body exactly as specified in the interface.
5. Use `data/equipment.json` as the reference and define the same three records
   in a static Python list. No file-reading code is needed.
6. Add a GET handler for the equipment collection that returns the list. Keep
   the data and both route handlers in `main.py`. For now, do not use
   `APIRouter`, `Depends`, a database or extra application layers.
7. Start the app from the exercise folder:

   ```bash
   python -m uvicorn app.main:app --reload
   ```

8. Request `/health` and `/equipment` using Postman or `/docs`. For each,
   inspect the status, `Content-Type` and JSON body. Then use **Try it out →
   Execute** for one operation in `/docs`. The supplied Postman collection and
   `requests.http` are optional aids.

## Check, explain and take the next step

Both operations should return 200 with the exact specified JSON bodies and a
JSON media type. The collection must contain all three records in order. A 404
at `/` is fine. Compare actual responses with your predictions and explain how
the decorator connects a request to a function and how its return value becomes
a response.

Now work without the numbered prompts: choose one request and trace it from
method and path, through the handler, to status, header and body. Add the
observations to the Exercise 01 section of `evidence/learning-log.md`. Commit
the working routes and evidence, then push to your own repository.

If stuck, check that the decorator uses the supplied `app`, the path starts
with `/`, and the handler returns a Python list/dictionary rather than a
JSON-looking string. Use `docs/troubleshooting.md` for environment/import
problems. Continue only when both routes work; Exercise 02 reorganises one
route while preserving its observable behaviour.
