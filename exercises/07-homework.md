# Homework — Add an equipment detail endpoint

**About one hour · independent implementation with selective hints**

Continue in the same repository and branch. Consolidate routes, path parameters,
error responses, generated documentation and tests. Read Exercise 05 first.

## Requirements

Add `GET /equipment/{equipment_id}` in your equipment router using the existing
static collection. Declare the parameter as an integer. Return the matching
object with HTTP 200 for an existing ID. For an absent integer ID, return HTTP
404 with exactly `{"detail": "Equipment not found"}`. Include a description of
the 404 in the operation's generated documentation.

Write `tests/test_equipment_detail.py` with two real checks: ID 2 returns the
correct Laser cutter object, and ID 999 returns the stated 404/error body.
Each test asserts both status and body. Preserve the health test and original
collection behaviour. No database, `Depends` or additional architectural
layers are required.

| Time | Work |
|---|---|
| 0–10 min | Read the primer, contract and existing code; predict both outcomes |
| 10–35 min | Implement the detail route and missing-resource behaviour |
| 35–50 min | Inspect generated docs and write/run the successful and missing-ID tests |
| 50–60 min | Recheck the original routes, update evidence, commit and push |

## Check your work

| Request/check | Expected evidence |
|---|---|
| `/equipment` | 200 and the unchanged three-item list |
| `/equipment/2` | 200 and the exact object specified in `design/expected-interface.md` |
| `/equipment/999` | 404 with the specified detail message |
| `/docs` and `/openapi.json` | Detail GET, integer path parameter and documented 404 |
| `python -m pytest -q` | At least the health, successful-detail and missing-detail checks pass |

A missing-item test alone could pass even if no detail route exists. Checking
the successful case and the precise error body gives stronger evidence.
Review both, and explain what the tests still do not establish.

Record results and a 3–4 sentence explanation in the homework section of the
learning log. Include how the path parameter reaches the function, why an
absent ID is 404, and how the implementation compares with your design.
Commit the implementation, tests and evidence, then push the branch.

## Hint ladder

1. Which variable contains the records, and which field identifies an item?
2. How can you compare the requested ID with the IDs in that collection?
3. Match the placeholder name to the function parameter. Use `HTTPException`
   for the error status; a plain error-shaped dictionary normally gives 200.

If unfinished after the hour, bring the smallest reproducible failure and
a note of what you tried. Review can address the missing step. The optional
limit activity is separate from homework completion.
