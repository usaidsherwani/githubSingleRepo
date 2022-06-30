---
title: Brief Introduction

---
<!-- FastAPI: Hello, World-->

Let's start with our fist program using FastAPI. We want to create a basic API that returns a string when we call a certain web path.

Create the file main.py:

```python
from fastapi import FastAPI
app = FastAPI()

@app.get("/")
def hello_world():
    return {"Hello": "World"}
{{copy filename='main.py'}}
```

Now let's start the ASGI server in the background. The goal here is to launch an asynchronous server gateway interface and run the application.

We're going to dig more into the details later, but for now, let's just run this command:

```bash
nohup uvicorn main:app --reload & 
{{ execute }}
```

Notice that in order to free up the terminal to use it later, we're using `nohup` and `&`.
In case you're not familiar with these commands, these are not related FastAPI but they are Linux commands to run a given command in background. In our case, we are running `uvicorn main:app --reload` in the background.

In the code above we imported the FastAPI module, we instanciated a FastAPI app `app = FastAPI()`, then we created the function `hello_world` that returns a disct `{"Hello": "World"}`. The function is decorated by the app name, followed by the HTTP verb used then the path to reach the resource `@app.get("/")`. This mean that sending a GET request to our application using the root path (`\`) should return `{"Hello": "World"}`. The default port of FastAPI is 8000.

Let's translate all of this to a curl request:

```bash
curl http://127.0.0.1:8000/
{{ execute }}
```