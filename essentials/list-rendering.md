# List Rendering

### ListBuilder

We can use ListBuilder widget to loop through an array in Python to render it on the screen.

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def __init__(self):
        self.items = ["Foo", "Bar"]

    def build(self):

        def display(index):
            return Text(self.items[index])

        return Container(
            children=[
                ListBuilder(
                    count=len(self.items),
                    builder=display
                )
            ]
        )

runApp(App())
```

Where the `count` parameter is how many times will the `builder` method will render.
