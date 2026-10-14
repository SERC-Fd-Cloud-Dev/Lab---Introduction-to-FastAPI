# 03 — Recognise dependency injection

**5 minutes · guided code reading, then individual explanation · no app changes**

FastAPI dependency injection lets a route declare what supporting value or
functionality it needs. FastAPI calls the dependency provider while handling a
request, then supplies the provider's result to the route. The route can use
that result without having to construct or look up the supporting resource
itself.

This is different from a *package dependency* in `requirements.txt`. A package
dependency is software installed into the Python environment (for example,
FastAPI itself). A FastAPI-injected dependency is a value or service supplied
to application code for a request. The shared word does not mean they are the
same mechanism.

## Trace the example

The tutor introduces `Depends` briefly. If working independently, read this
configuration-style example; it is not part of the Equipment Inventory app:

```python
from typing import Annotated
from fastapi import Depends, FastAPI

demo = FastAPI()

def get_site_name():
    return "North campus"

@demo.get("/site")
def read_site(site_name: Annotated[str, Depends(get_site_name)]):
    return {"site": site_name}
```

Trace one request to `/site` in order:

1. FastAPI matches the GET request to the decorated route handler.
2. The handler declares a `site_name` parameter with `Depends(get_site_name)`.
3. FastAPI calls `get_site_name` and supplies its returned value to that
   parameter before calling the handler.
4. The handler uses the supplied value in its response.

The provider is an ordinary function; `Depends` marks it for FastAPI's request
handling. This example is for reading only. Do not copy it into the application
or create a dependency module or test.

## Explain it yourself

In `evidence/learning-log.md`, explain in your own words who calls the provider,
how its value reaches the route, and how this differs from installing a package
with pip. Name one later use, such as sharing a database session or authenticated
user information across route handling.

Finish independently: point to the example's provider, injected parameter and
route response, then explain why no `Depends` implementation is needed for the
current static-data exercises. There is no application coding checkpoint here.
