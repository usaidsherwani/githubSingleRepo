---
title: "The operation decorator"

---
<!--The operation decorator-->

We used the `@app.get("/")` decorator which works with GET requests, however there are other request types that we can use. 
These are the common ones: GET, POST, PUT, DELETE.

To implement these in FastAPI, we can use them this way:

```
@app.post()
@app.put()
@app.delete()
```

There are also other operators that are less used (like OPTIONS and HEAD) and they can be used with these decorators:

```
@app.options()
@app.head()
@app.patch()
@app.trace()
```

Let's go through an example to understand how to use the decorator. Previously, we used `@app.get("/")` and `curl http://127.0.0.1:8000/` curl command to call the `/` path.

`curl http://127.0.0.1:8000/` is the equivalent of `curl -X GET http://127.0.0.1:8000/`. In other words, when you don't mention the HTTP verb, GET will be used by default.

Let's change the root path `/` to use POST:

{{copy filename='main.py'}}
```python
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.post("/")
{{ /highlight }}
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

If you execute a curl with a GET verb using `curl http://127.0.0.1:8000/` or `curl -X GET http://127.0.0.1:8000/` you'll get this error `{"detail":"Method Not Allowed"}`:

{{ execute }}
```
curl -X GET http://127.0.0.1:8000/
```
{{ /execute }}

The API will only respond when you use a POST HTTP verb:

{{ execute }}
```
curl -X POST http://127.0.0.1:8000/
```
{{ /execute }}

The operation decorator is mandatory if you want the function to be called when the client request a path. In a FastAPI program, we usually have different functions with different paths and methods.