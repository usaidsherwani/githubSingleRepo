---
title: Using Docker to Run the Web App

---
<!--Synchronous v/s Asynchronous-->

If you're not familiar with the definitions of "synchronous" and "asynchronous", we're going to explain them here.

To simplify these two concepts, let's consider the following definitions.

When the interpreter sends a synchronous request, it stops executing all the other requests until it get a response from the HTTP server. (The response can also be an error or a timeout). At this stage, the whole program is bloked and is waiting for the request to complete and the web server to send back a HTTP response.

In the case of an asynchronous request, when the interpreter executes a request it send it and forget about it, then move to the next request to execute. In other words, the program does not need to wait for the webserver and can execute more requests during a given period, compared to the synchronous program. Even if the request is not completed, a Python program working with an asynchronous webserver can move to the next request.

There's a main goal behind adopting asynchronousity which is making Python faster. The consequences of this increased speed will reflect on the quality of programs we can build and the end user experience.

Uvicorn, the server we are using to launch a FastAPI program, is an ASGI server implementation, using [uvloop](https://github.com/MagicStack/uvloop) and [httptools](https://github.com/MagicStack/httptools).

Uvicorn uses uvloop, a drop-in replacement of the built-in asyncio event loop, which makes it an asynchronous web server.

httptools, a Python binding for the nodejs HTTP parser, makes Uvicorn faster than many other Python webservers.