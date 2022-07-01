---
title: The Dockerfile

---
<!--ASGI vs WSGI -->

Previsouly in this scenario, we used `uvicorn main:app --reload` to start our FastAPI application. This launches an ASGI server.
If you already worked with Django or Flask frameworks you had certainly used an WSGI server. So you might have in mind this question: What's the difference between the two servers? 

The WSGI, if you're not familiar with this term, is the Python standard for compatibility between web servers, frameworks, and applications

The ASGI official documentation replie to the previous question:

> ASGI is a spiritual successor to WSGI, the long-standing Python standard for compatibility between web servers, frameworks, and applications. WSGI 
> succeeded in allowing much more freedom and innovation in the Python web space, and ASGI’s goal is to continue this onward into the land of asynchronous > Python.

The keyword here is "asynchronous".

A WSGI application takes a single request and returns a single response at a time. So a WSGI application is necessaraly synchronous, which create limits to create and work with long lived connections like websocket-based applications. Even when you make an WSGI application asynchronous it will be always limited by the fact that there will be always a single path to send and recevie a request.

ASGI solves this problem. It name stands for **Asynchronous** Server Gateway Interface.