---
title: "Back to the basics"

---
<!-- Back to the basics -->

Back to the basics, let's understand when we use each of the common HTTP methods.

Basically, each HTTP method is commonly used to perform a certain type of actions:

- POST is used to create data.
- GET is used to read data.
- PUT is used to update data.
- DELETE is used to delete data.

The other less common methods act in the same way:

- HEAD is identical to GET except that the server must not return a message-body in the response. It must return metainformation like the content length, type, date and other information like the server name and the response status (200, 404, 500..etc).
- PUT is "the opposite" of GET. GET requests a resource while PUT places the resource in a remote directory.
- PATCH is conceived to partially update a remote resource.
- OPTIONS is used to describe the communication options for the target resource. In other words, it is only used to query information about ways to interact and consume a remote resource.

The [HTTP Request Method registry](https://www.iana.org/assignments/http-methods/http-methods.xhtml) lists 39 HTTP verbs in total.
