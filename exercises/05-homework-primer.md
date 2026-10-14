# 05 — Prepare for the detail-endpoint homework

**3 minutes · tutor worked example · read before starting homework**

A path parameter identifies one resource. In a path such as `/rooms/{room_id}`,
the value in braces is passed to the function parameter with the same name.
Annotating it as `int` asks FastAPI to interpret and validate it as an integer.

This small example uses **rooms**, not the equipment solution. It shows the
parameter/error mechanism; deciding how to search your collection remains your work.

```python
from fastapi import FastAPI, HTTPException

demo = FastAPI()

@demo.get("/rooms/{room_id}", responses={404: {"description": "Room not found"}})
def read_room(room_id: int):
    if room_id != 10:
        raise HTTPException(status_code=404, detail="Room not found")
    return {"id": 10, "name": "Studio"}
```

`raise HTTPException(...)` sets an HTTP error response. Returning a dictionary
containing an error message would normally still return 200. The `responses`
metadata documents the possible 404; it does not implement the missing-resource
branch. A missing integer ID and a non-integer path are different cases.

When your equipment router has prefix `/equipment`, its detail route suffix
uses `/{equipment_id}`. Keep the prefix in one place. Read the homework
requirements and predict the successful and missing-ID responses before coding.
