# 02 — Organise the resource route with APIRouter

**15 minutes including tutor demonstration · guided refactor, independent check**

Starting point: both Exercise 01 routes work in `app/main.py`, and you have
recorded their responses. This refactor changes where the equipment route is
defined, not what clients observe.

## What a router does

`APIRouter` is a FastAPI object for grouping related route handlers. It lets a
larger application organise routes by resource or feature while keeping the
same application. A router can declare a shared prefix such as `/equipment`;
FastAPI combines that prefix with each route's suffix. An empty suffix means
the collection path is exactly `/equipment`, not `/equipment/equipment`.

Creating a router defines a group of operations. Registering it with
`app.include_router(...)` adds those operations to the application. Importing
the Python module makes its objects available, but by itself does not register
its routes. The tutor demonstrates this structure with Shuttle Stops first.

For comparison, this small **rooms** example shows the two distinct places
involved. It is a shape to read, not code to add to your equipment app:

```python
# In a rooms router module
from fastapi import APIRouter

router = APIRouter(prefix="/rooms", tags=["rooms"])

@router.get("")
def list_rooms():
    return [{"id": 10, "name": "Studio"}]
```

```python
# In the application module
from app.routers import rooms

app.include_router(rooms.router)
```

The router decorator's empty suffix combines with `/rooms` to make the
collection path `/rooms`. The application includes the router once so FastAPI
can serve the route. In your refactor, use the tutor's demonstrated structure
and the already-working equipment handler and data.

## Follow the refactor — about 10 minutes

1. Create `app/routers/`, an empty `app/routers/__init__.py`, and
   `app/routers/equipment.py`. These make the router module importable.
2. In `equipment.py`, import `APIRouter` and create a router with prefix
   `/equipment` and tag `equipment`, following the tutor's example.
3. Move the equipment list and collection handler from `main.py` into
   `equipment.py`. Attach the handler to the router, using an empty path suffix
   so the combined collection path remains `/equipment`.
4. In `main.py`, import the equipment router and register it with the app.
   Keep app creation and the health handler in `main.py`.
5. Remove the old equipment list and handler from `main.py`. There should be
   one collection route, not both the old app route and the router route.

## Verify and explain — about 5 minutes

Request `/health` and `/equipment`. Compare their exact paths, statuses and
bodies with Exercise 01, and check the equipment tag in `/docs`. The interface
should be unchanged. Add the before/after comparison to
`evidence/learning-log.md`.

Then independently choose which files and definitions to inspect to verify
there is exactly one collection route and that its path is still `/equipment`.
Without following the numbered instructions, explain where the router is
created and where it is registered. Point to evidence that importing alone
would not register it, and name one benefit of grouping resource operations.
Commit and push a meaningful increment.

## If stuck

- A 404 after refactoring: check the module import and `include_router` call.
- `/equipment/equipment`: the route suffix repeats the router prefix.
- A redirect from `/equipment` to `/equipment/`: check the collection suffix;
  the expected path is `/equipment` exactly.
- A circular import: `equipment.py` should not import `app` from `main.py`.

This refactor introduces route organisation, not dependency injection. Routers
can group routes without using `Depends`.
