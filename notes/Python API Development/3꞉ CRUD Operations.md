---
attachments: [Clipboard_2022-08-09-21-28-46.png]
tags: [Notebooks/Python API Dev]
title: '3: CRUD Operations'
created: '2022-08-09T13:28:20.391Z'
modified: '2022-08-11T11:34:46.917Z'
---

# 3: CRUD Operations

![](@attachment/Clipboard_2022-08-09-21-28-46.png)


### POST (CREATE)
- send 201 if created
- server adds ID
- when a new resource is created, send back newly-created resource
```py
@app.post("/posts")
def get_posts(post: Post):
    post_dict = post.dict()
    post_dict["id"] = randrange(0, 100000000)
    posts.append(post_dict)
    return {"data": post_dict}
```

### GET (READ)
- send 200 if ok
```py
@app.get("/posts")
def get_posts():
    return {"data": posts}
```

### GET/ID (READ ONE)
- send 404 if resource isn't found
```py
# passing a path parameter
# validate that id is an int
@app.get("/posts/{id}")
def get_post(id: int, response: Response):
    post = find_post(id)
    if not post:
        raise HTTPException(status_code=status.HTTP_404_NOT_FOUND, detail=f"Post with id {id} was not found")
    return {"post detail": post}
```

### PATCH (UPDATE)
- send 404 if not found
```py
@app.put("/posts/{id}")
def update_post(id: int, post: Post):
    index = find_post_index(id)

    if index is None:
        raise HTTPException(status_code=status.HTTP_404_NOT_FOUND, detail=f"Post with id {id} does not exist")

    post_dict = post.dict()
    post_dict['id'] = id
    posts[index] = post_dict

    return {"data": post_dict}
```

### DELETE (DELETE)
- send 204 after deleting
- send 404 if not found
```py
@app.delete("/posts/{id}", status_code=status.HTTP_204_NO_CONTENT)
def delete_post(id: int):
    post = find_index_post(id)

    return Response(status_code=status.HTTP_204_NO_CONTENT)
```

#### Changing response status codes

Import `Response` and `Status` from FastAPI

```py
from fastapi import FastAPI, Response

if not post:
  response.status_code = status.HTTP_404_NOT_FOUND
  return {"message": f"post with id: {id} was not found"}
```

OR

use `HTTPException`

```py
from fastapi import FastAPI, Response, HTTPException

if not post:
  raise HTTPException(status_code=status.HTTP_404_NOT_FOUND, detail=f"Post with id {id} was not found")
```

#### Changing default status code
```py
@app.post("/posts", status_code=status.HTTP_201_CREATED)
```
