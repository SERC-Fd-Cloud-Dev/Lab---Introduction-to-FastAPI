# Optional challenge — Limit the collection response

Add a `limit` query parameter to `GET /equipment` after the core work is complete.
This is extra practice, not a homework completion requirement.

- With no parameter, return all three original records.
- `?limit=1` returns only the first record.
- A positive limit larger than the collection returns all available records.
- Keep the detail route and existing tests working.

Predict each result first, choose a reasonable approach, and write a small
check for the new behaviour. Think about zero/negative values, but detailed
validation constraints are a later lesson. Explain the boundary you chose.

Record the optional result in the learning log and commit it separately.
