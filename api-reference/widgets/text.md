# Text

This is used to create a text on the screen. This is equivalent to `p` tag in HTML. Basically, anything you can do with `p` tags are also possible in Container widget with `props` bindings.&#x20;

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Container(
            children=[
                Text("Hello, World!"),
                Text("Hello, Mom!")
            ]
        )

runApp(App())
```

## Reference

### Properties

* textContent (positional) -> string
* props -> dictionary of properties used to access HTML built-ins.
* className -> string
