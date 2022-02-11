# Class and Props Bindings

You sometimes need to access Class and HTML Props for inline styling or creating a new attribute to a widget.

It's also possible that in PyFyre:

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def __init__(self):
        self.active = True
        self.hasError = False

    def build(self):
        return Container(
            props={
                "id": "container",
                "style": "background-color: black"
            },
            className=f"{'active' if self.active else ''} {'text-danger' if self.hasError else ''}"
        )

runApp(
    App(),
    mount="app-mount"
)
```

Fortunately, Python supports lovely string interpolation with F-string formatting.

You can access widget's attributes on the DOM on `props` parameter. It's a Python dictionary where the `key` is the name of the attribute and the `value` is the value of the attribute.

If the attribute requires no value, you can just set the value `None`:

```python
return Container(
    props={
        "modal-open": None 
    },
)
```
