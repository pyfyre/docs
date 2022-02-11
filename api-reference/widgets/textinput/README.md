# TextInput

This is used to get input from users on the screen.

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def __init__(self):
        self.controller = TextInputController()
        self.text = ""

    def build(self):

        def output(ev):
            self.text = self.controller.value
            self.update()

        return Container(
            children=[
                TextInput(controller=self.controller),
                Button(f"Output: {self.text}", onClick=output)
            ]
        )

runApp(App())
```

## Reference

### Properties

* controller -> [TextInputController ](textinputcontroller.md)(used to access and leverage TextInput's properties, attributes, and methods)
* props -> dictionary of properties used to access HTML built-ins.
* className -> string
