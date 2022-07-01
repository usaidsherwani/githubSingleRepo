---
title: "Using more HTTP methods"

---
<!-- Using more HTTP methods -->

We tested changing GET by a POST. You can use the operation that you wish. Let's see some examples:

Use a PUT method:

{{copy filename='main.py'}}
```python
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.put("/")
{{ /highlight }}
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

Run a curl:

{{ execute }}
```
curl -X PUT http://127.0.0.1:8000/
```
{{ /execute }}

Let's use a DELETE method:

{{copy filename='main.py'}}
```
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.delete("/")
{{ /highlight }}
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

Run a curl:

{{ execute }}
```
curl -X DELETE http://127.0.0.1:8000/
```
{{ /execute }}