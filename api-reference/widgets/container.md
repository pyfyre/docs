# Container

This is used to wrap widgets in a PyFyre app. This is equivalent to `div` tag in HTML. Basically, anything you can do with `div` tags are also possible in Container widget with `props` bindings.&#x20;

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

* children -> list of Widgets
* props -> dictionary of properties used to access HTML built-ins.
* className -> string
