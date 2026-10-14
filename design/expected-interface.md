# Expected Equipment Inventory interface

Use these observable requirements to check your implementation. Keep the exact
paths stable through the router refactor; use JSON for the response bodies.

| Stage | Method and path | Status | Expected representation |
|---|---|---|---|
| Core | `GET /health` | 200 | `{"status": "ok"}` |
| Core | `GET /equipment` | 200 | All three records in `data/equipment.json`, as a JSON array in the supplied order |
| Homework | `GET /equipment/2` | 200 | `{"id": 2, "name": "Laser cutter", "location": "Workshop"}` |
| Homework | `GET /equipment/999` | 404 | `{"detail": "Equipment not found"}` |

The collection's `id`, `name`, and `location` fields should retain their supplied
values. An unknown integer ID is an absent resource. A non-integer path value
is a different input case; recognising FastAPI's automatic 422 response is optional
here, with detailed validation reserved for a later lesson.

`/` may return 404: no root route is required. A basic health route proves that
the application can serve that request; it does not establish database readiness,
cloud deployment, capacity or full service health.

Copy your OpenAPI design from the REST/OpenAPI sub-lesson into `openapi.yaml`.
The supplied YAML is only a valid minimal starting shell. If your design describes
future detail/create operations, keep those clearly identified as planned.
They will not appear in FastAPI's generated document until implemented.

If your earlier contract is unavailable, use this table for the initial comparison
and record that limitation. Bring or reconstruct the small design contract during
catch-up. Do not replace your design with generated JSON and call that a comparison.
