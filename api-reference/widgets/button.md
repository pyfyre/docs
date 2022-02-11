# Button

This is used to create a button on the screen. This is equivalent to `button` tag in HTML. Basically, anything you can do with `button` tags are also possible in Button widget with `props` bindings.&#x20;

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):

        def hello(ev):
            print("Hello!")

        return Container(
            children=[
                Button("Hello, Mom!", onClick=hello)
            ]
        )

runApp(App())
```

## Reference

### Properties

* textContent (positional) -> string
* props -> dictionary of properties used to access HTML built-ins.
* className -> string

### Methods

onClick() -> HTML Button Event
