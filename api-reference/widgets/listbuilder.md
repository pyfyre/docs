# ListBuilder

This is used to directly render a list of items based on an array.&#x20;

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):

        def texts(index):
            return Text(f"Index: {index}")

        return Container(
            children=[
                ListBuilder(
                    count=5,
                    builder=texts
                )
            ]
        )

runApp(App())
```

## Reference

### Properties

* count -> int (how many times will the builder render?)
* props -> dictionary of properties used to access HTML built-ins.
* className -> string

### Methods

render(index) -> Widget that will render `count` times on the screen.
