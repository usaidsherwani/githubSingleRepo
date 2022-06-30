---
title: "Using different paths"

---
<!--Using different paths-->

The first example used a single path: `/`:


```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/")
def root():
    return {"message": "Hello World"}
```    

In this step, we are going to understand how to use other paths. Let's update the path of the `root` function:

{{copy filename='main.py'}}
```python
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.get("/test")
{{ /highlight }}
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

When you execute the `curl -X GET http://127.0.0.1:8000/`, the API will return `{"detail":"Not Found"}`. Let's use the right path here:

{{ execute }}
```
curl -X GET http://127.0.0.1:8000/test
```
{{ /execute }}

You are supposed to see `{"message":"Hello World"}` returned by the webserver.
In the same way, we can create multiple functions for different paths:

```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/test1")
def test1():
    return {"message": "test"}
@app.get("/test2")
def test2():
    return {"message": "test"}
@app.get("/test3")
def test3():
    return {"message": "test"}
```