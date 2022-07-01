---
title: "Multiple paths for the same function"

---
<!--Multiple paths for the same function-->

We saw that we can use multiple paths in a single API, which is normal if you want to use FastAPI to build APIs. Let's use the following example:

{{copy filename='main.py'}}
```
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
{{ /copy }}

Let's execute some commands to make sure the above code works:

{{ execute }}
```
curl -X GET  http://127.0.0.1:8000/test1
curl -X GET  http://127.0.0.1:8000/test2
curl -X GET  http://127.0.0.1:8000/test3
```
{{ /execute }}

We should be able to see the same message (`{"message": "test"}`) thrice. However, there's a simple way we can use to rewrite the previous API:

Let's do it:

{{copy filename='main.py'}}
```
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.get("/test2")
@app.get("/test1")
@app.get("/test3")
def test1():
    return {"message": "test"}
{{ /highlight }}    
```
{{ /copy }}

Let's execute and see:

{{ execute }}
```
curl -X GET  http://127.0.0.1:8000/test1
curl -X GET  http://127.0.0.1:8000/test2
curl -X GET  http://127.0.0.1:8000/test3
```
{{ /execute }}

We should be able to see the same message (`{"message": "test"}`) thrice too.

The conclusion is that a single function may have multiple paths. We can even have multiple paths mapped to the same function but with different methods. Let's try this:

{{copy filename='main.py'}}
```
from fastapi import FastAPI
app = FastAPI()
@app.get("/test1")
{{ highlight }}
@app.post("/test2")
@app.delete("/test3")
{{ /highlight }}
def test1():
    return {"message": "test"} 
```
{{ /copy }}

Let's execute and see:

{{ execute }}
```
curl -X GET  http://127.0.0.1:8000/test1
curl -X POST  http://127.0.0.1:8000/test2
curl -X DELETE  http://127.0.0.1:8000/test3
```
{{ /execute }}

Conclusion, paths are flexible: A function may have different paths and use different operations at the same time.