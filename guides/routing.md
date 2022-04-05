# Routing

Routing is of course important to applications. PyFyre helps you make Single-Page Applications easily.

### Simple Routing from scratch

```python
from pyfyre.widgets import *
from pyfyre.router import Router
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Router(
            routes={
                "/": Home(),
                "/about": About()
            }
        )

class Home(UsesState):
    def build(self):
        return Text("Welcome Home!")

class About(UsesState):
    def build(self):
        return Text("Wanna know about us?")

runApp(
    App(),
    mount="app-mount"
)
```

### Dynamic Routing

PyFyre also allows you to access path query parameters.

```python
from pyfyre.widgets import *
from pyfyre.router import Router
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Router(
            routes={
                "/users": Users(),
                "/users/:slug": UserProfile()
            }
        )

class Users(UsesState):
    def build(self):
        return Text("List of users...")

class UserProfile(UsesState):
    def build(self):
        slug = Router.query()['slug']

        return Text(f"User: {slug}")

runApp(
    App(),
    mount="app-mount"
)
```
