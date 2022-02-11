# Display Text on the screen

Display a Text on the screen is easy. With `Text` widget, you can create a text (a.k.a `p` tag on HTML) and PyFyre takes it care for you to add it into the DOM.

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class MyWebpage(UsesState):
    def build(self):
        return Text("Hello, World!")

runApp(MyWebpage())
```

And that's it!
