# Clickable

Every widgets is not Clickable (except Button). To make the Widget clickable, you need to wrap them with this `Clickable` widget.

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):

        def hello(ev):
            print("Hello!")

        return Clickable(
            Container(
                children=[
                    Text("Hello, Mom!")
                ]
            ),
            onClick=hello
        )

runApp(App())
```

If that feels weird for you, alternatively, you can explicitly add `bind` parameter name to it.

```python
return Clickable(
    bind=Container(
        children=[
            Text("Hello, Mom!")
        ]
    ),
    onClick=hello
)
```

## Reference

### Properties

* bind (positional) -> Widget to wrap as a clickable
* props -> dictionary of properties used to access HTML built-ins.
* className -> string

### Methods

onClick() -> HTML Event
