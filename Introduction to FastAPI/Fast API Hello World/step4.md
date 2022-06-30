---
title: Brief Introduction

---
<!--The FastAPI app object-->

In the first "Hello, world" API we created, we used the following code:

```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/")
def hello_world():
    return {"Hello": "World"}
```

In order to work with FastAPI, the line `app = FastAPI()` which we use to call FastAPI framework in a Python application.
Usually, we use the name `app` but it's possible to change this:

{{copy filename='main.py'}}
```python
from fastapi import FastAPI
{{highlight}}
my_application = FastAPI()
@my_application.get("/")
{{/highlight}}
def hello_world():
    return {"Hello": "World"}    
```
{{/copy}}

Remember that we launched our web server in the background using `uvicorn main:app --reload`. When we change `app` to `my_application`, we should also change how we run the Uvicorn server.

Stop the running server, then launch a new one:

{{ execute }}
```
kill %1
nohup uvicorn main:my_application --reload &
```
{{ /execute }}

Let's run a curl to make sure everything works like expected:

{{ execute }}
```
curl http://127.0.0.1:8000/
```
{{ /execute }}