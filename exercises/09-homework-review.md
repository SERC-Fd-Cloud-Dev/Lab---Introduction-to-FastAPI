# Homework review — Diagnose and improve the API

**One-hour review session · use your existing repository and learning log**

| Time | Activity | Evidence to record |
|---|---|---|
| 0–10 min | Answer the retrieval questions below individually, then compare reasoning | Short answers in the learning log |
| 10–25 min | Take turns demonstrating the detail route, generated docs and tests | One strength and one actionable improvement |
| 25–40 min | Investigate a common routing, status, import or test problem with the tutor | Specific symptom and likely cause |
| 40–55 min | Correct one weakness, rerun the affected checks and full tests | Before/after result, commit and push |
| 55–60 min | Explain the boundary between the route and future data access | Readiness answer in the log |

If working independently, use the troubleshooting guide to select a reproducible
problem or an improvement from your own results. Do not invent a failure if the
API behaves correctly: improve a weak explanation, test or documentation gap instead.

## Retrieval and diagnosis

Use a concrete example to justify each answer. Concise answers are enough.

1. A resource is available at `/rooms/7`. Which method retrieves it? Should repeating
   the request change its intended state?
2. A DELETE returns 204 first and 404 when repeated. Can it still be idempotent?
3. An ordered collection has IDs 1–5. Which IDs does `limit=2&offset=2` select?
4. What does an OpenAPI contract communicate beyond a URI list?
5. Your design includes POST, but generated OpenAPI lists only GET. Give a likely
   explanation and an appropriate next action.
6. A router uses prefix `/equipment` and decorator `@router.get("/equipment")`.
   Which path does that define?
7. A correct router module still gives 404 for every request. Which setup step
   could be missing?
8. A route returns `{"detail": "Equipment not found"}` without changing the status.
   Why might a client misinterpret it? Which mechanism sets an HTTP error?
9. A health test asserts only 200. What assertion would catch a changed JSON body?
10. How does `Depends(get_site_name)` differ from installing FastAPI with pip?
    Who calls the provider?

Attempt the questions before opening the feedback.

<details>
<summary>Retrieval feedback</summary>

1. GET retrieves the representation; its intended effect does not change the resource.
2. Yes. Idempotency concerns the intended effect on server state, not identical responses.
3. IDs 3 and 4, using a zero-based offset of two and a limit of two.
4. Methods, parameters, responses, media types and schemas can describe the interface.
5. POST may be planned but not implemented. Compare the design and code before deciding
   whether to add it now or leave it explicitly planned for a later stage.
6. `/equipment/equipment`: the prefix and operation suffix are combined.
7. The application may not have called `include_router` for that router.
8. A normal JSON return usually gives 200, suggesting success. Raise `HTTPException`
   with the required error status and detail.
9. Assert the exact expected JSON, as well as the status.
10. Pip installs packages in the environment; FastAPI calls the provider and supplies
    its result while handling the route.

</details>

## Readiness question

When the static collection is replaced by a database, which responsibility should
remain with the HTTP route and which belongs to data-access code? Explain the
boundary in words; no persistence implementation is required yet.

The route should handle the HTTP-facing interface and translate outcomes to
responses; the data-access code should retrieve/store records. Later lessons
develop that boundary. Record your answer and the improvement you made in the log.
