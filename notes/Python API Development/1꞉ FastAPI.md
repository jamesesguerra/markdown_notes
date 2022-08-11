---
tags: [Notebooks/Python API Dev]
title: '1: FastAPI'
created: '2022-08-09T06:31:17.418Z'
modified: '2022-08-09T12:13:10.157Z'
---

# 1: FastAPI

#### Install FastAPI and all dependencies
```sh
pip install fastapi[all]
```

#### Show all packages installed
```sh
pip freeze
```

#### Import FastAPi
```py
# main.py
from fastapi import FastAPI
```

#### Install `autopep8`
```sh
pip install -U autopep8
```

#### Start dev server
```sh
# uvicorn fileName:appName
uvicorn main:app --reload
```

#### Extracting data from body
```py
from fastapi.params import Body

@app.post("/post")
def create_post(payload: dict = Body(...)):
  print(payload)
```
