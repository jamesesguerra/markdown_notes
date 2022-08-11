---
tags: [Notebooks/Python API Dev]
title: '2: pydantic'
created: '2022-08-09T12:12:20.761Z'
modified: '2022-08-09T14:37:20.011Z'
---

# 2: pydantic

__Schema__ - Defining what the data should look like; somewhat like a contract; working with an API entails explicitly defining what the data should look like so the frontend can send the data you expect. It's telling the frontend what the data should look like, what we're expecting.

#### Why we need Schema
- It's a pain to get all the values from the body
- The client can send whatever data they want (no validation)
- We want to force the client to send data in a schema we expect 

#### importing `BaseModel` and `Optional`
```py
from pydantic import BaseModel
from typing import Optional
```

`Post` model:
```py
# pydantic validates the data using the model
class Post(BaseModel):
  title: str
  content: str
  published: bool = True # default value
  rating: Optional[int] = None # completely optional field / no default value

# make sure body comes in with the right schema
@app.get("/post")
def create_post(post: Post):
  # some code
```

#### Converting pydantic model into a Python dictionary
```py
post.dict()
```
