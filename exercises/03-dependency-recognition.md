# 03 — Recognise dependency injection

**5 minutes · code reading and explanation · no application changes**

Watch the tutor's short `Depends` preview. A dependency provider is a function
whose result FastAPI can supply to a route. This differs from installing
a Python package with pip.

If catching up independently, read this different, configuration-style example:

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

Read it here; do not copy it into your Equipment Inventory application.
Answer briefly in `evidence/learning-log.md`:

1. Who calls `get_site_name`, and how does its result reach `read_site`?
2. How does `Depends` differ from a dependency listed in `requirements.txt`?
3. Name a later problem for which a route could need shared supporting functionality.

**Feedback:** FastAPI calls the provider and supplies its returned value to the
route parameter. Package dependencies are libraries installed into an environment;
dependency injection supplies functionality/data while handling a request.
Database sessions and authenticated-user information are later examples.

No `dependencies.py`, student `Depends` code or dependency test is required.
