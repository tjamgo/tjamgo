<div align="center">
  <img src="https://raw.githubusercontent.com/tjamgo/tjamgo/main/docs/logo.jpg" alt="Tjamgo" width="300">
</div>

# Tjamgo: Python Web Framework built for learning purpose

![Static Badge](https://img.shields.io/badge/purpose-learnig-green)
![PyPI Version](https://img.shields.io/pypi/v/tjamgo)

Tjamgo is a python web framework built for learning.

It's a WSGI framework and can be used with any WSGI application server such as Gunicorn.

## Installation

```shell
pip install tjamgo
```

## How to use it

### Basic usage:

```python
from tjamgo.app import TjamgoApp

app = TjamgoApp()

@app.route("/home", allowed_methods=["get"])
def home(request, response):
    response.text = "Hello from the home page"


@app.route("/about", allowed_methods=["put"])
def about(request, response):
    response.text = "Hello from the about page"


@app.route("/hello/{name}")
def greeting(request, response, name):
    response.text = f"Hello {name}"


@app.route("/books")
class Books:
    def get(self, request, response):
        response.text = "Books page"

    def post(self, request, response):
        response.text = "Endpoint to create a book"


def new_handler(req, resp):
    resp.text = "From new handler"


app.add_route("/new-handler", new_handler)


@app.route("/template")
def template_handler(req, resp):
    resp.body = app.template(
        "home.html",
        context={"new_title": "tjamgo", "new_body": "Best framework"}
    )
```
