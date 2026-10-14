# 02 — Organise the resource route with APIRouter

**15 minutes, including tutor demonstration · guided**

Starting point: Exercise 01's working single-file application and recorded
responses. A router groups related operations as the application grows.
This refactor should preserve the HTTP interface.

## Guided refactor

1. Create `app/routers/`, an empty `app/routers/__init__.py`, and
   `app/routers/equipment.py`.
2. In `equipment.py`, import `APIRouter` and create a router with prefix
   `/equipment` and tag `equipment`, following the tutor's Shuttle Stops pattern.
3. Move your equipment list and resource function from `main.py` to that module.
   Replace the resource decorator with a router decorator. Use an empty suffix
   for the collection: the prefix already contains `/equipment`.
4. In `main.py`, import the equipment module from `app.routers`, and register
   its router with the application's `include_router` method.
5. Keep app creation and the health route in `main.py`. Remove the original
   equipment function/data from it; do not leave duplicate route definitions.
6. Request `/health` and `/equipment` again. Compare the exact paths, statuses
   and JSON bodies with Exercise 01. Check the equipment tag in `/docs` too.

## Check and explain

The same two requests should still work, with the same bodies. Explain where
the router is created, where it is registered, and why importing a module alone
does not register its routes. Explain one advantage of grouping a resource's routes.

Record the comparison in `evidence/learning-log.md`. Commit and push a meaningful
increment, for example **Group equipment routes in an APIRouter**.

## If stuck

- 404 after refactor: check the module import and `include_router` registration.
- `/equipment/equipment`: the resource path was repeated after the prefix.
- Redirect to `/equipment/`: check the collection suffix. The agreed path is
  `/equipment` exactly, without relying on a trailing-slash redirect.
- Circular import: the equipment module should not import `app` from `main.py`.

You have not added dependency injection. Routers can organise routes on their own.
