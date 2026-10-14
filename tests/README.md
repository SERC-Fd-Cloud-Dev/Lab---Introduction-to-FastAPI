# Tests you will write

Exercise 04: create `test_health.py` and a real `test_health_returns_ok` test.
Homework: create `test_equipment_detail.py` with successful and missing-item checks.
Import the app from `app.main` and use FastAPI's TestClient.

Run `python -m pytest -q` from the exercise folder. TestClient does not need a
running Uvicorn server. There are no completed tests in the starting repository:
an initial pytest run collects no tests and exits with code 5.

Do not turn a missing implementation into a passing check by skipping it,
removing assertions or changing the expected contract. Diagnose the result.
