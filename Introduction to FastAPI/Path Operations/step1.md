---
title: "Introduction"

---
<!--Introduction-->

When you navigate the web, you'll use URLs like:

- https://www.google.com/search
- https://en.wikipedia.org/wiki/Main_Page

The `/search` in `https://www.google.com/search` and the `/wiki/Main_Page` in `https://en.wikipedia.org/wiki/Main_Page` are called paths.
In the following URL `https://www.example.com/`, the `/` is also the path.

In this scenario, our goal is to understand how to use these paths in FastAPI. 

Let's start with launching Uvicorn server in the background:

{{ execute }}
```
nohup uvicorn main:app --reload & 
```
{{ /execute }}

Now, let's create this simple "Hello, world" API:

{{copy filename='main.py'}}
```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/")
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

This program exposes the path `/` to the API user. This is done using a decorator (`@app.get("/")`) that tells FastAPI that the function `root` should be called when the path `/` is requested using a GET operation.

You can test this using:

{{ execute }}
```
curl http://127.0.0.1:8000/
```
{{ /execute }}