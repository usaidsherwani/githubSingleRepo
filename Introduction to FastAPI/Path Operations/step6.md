---
title: "The trailing slash"

---
<!--The trailing slash-->

Previously we executed the command `curl -X GET http://127.0.0.1:8000/test` and the API replied correctly.

What will happen when we use the path `/test/` instead of just `/test`? 

Let's see:

```
curl -X GET http://127.0.0.1:8000/test/
{{ execute }}
```

You should see nothing returned, so let's examine the headers using the same path:

```
curl -I http://127.0.0.1:8000/test/
{{ execute }}
```

By executing the command above, we realize that we have a temporary redirection. The response code is 307.
In order to follow the redirection, we can use the `-L` flag with curl (`curl -L <url>` or `curl --location <url>`).

```
curl -X GET -L http://127.0.0.1:8000/test/
{{ execute }}
```

As you can see, the curl command followed the redirection and the API is now returning a response.

In the same way, if our application was using `/test/` instead of `/test` in the decorator, FastAPI will redirect us.

Update your code:

{{copy filename='main.py'}}
```
from fastapi import FastAPI
app = FastAPI()
{{ highlight }}
@app.get("/test/")
{{ /highlight }}
def root():
    return {"message": "Hello World"}
```
{{ /copy }}

Let's test the path as it is:

```bash
curl -X GET  http://127.0.0.1:8000/test/
{{ execute }}
```

Then test without the trailing slash and by adding the redirection flag `-L`:

```bash
curl -X GET  -L http://127.0.0.1:8000/test
{{ execute }}
```

The trailing slash in FastAPI can be removed from the path used in the decorator. Calling the path with a trailing slash or without has no importance at the condition of following the redirections.