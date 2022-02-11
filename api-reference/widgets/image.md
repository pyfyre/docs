# Image

This is used to create an image on the screen. This is equivalent to `img` tag in HTML. Basically, anything you can do with `img` tags are also possible in Image widget with `props` bindings.&#x20;

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Container(
            children=[
                Image("https://variety.com/wp-content/uploads/2021/07/Rick-Astley-Never-Gonna-Give-You-Up.png?w=1024")
            ]
        )

runApp(App())
```

## Reference

### Properties

* src (positional) -> string image link
* props -> dictionary of properties used to access HTML built-ins.
* className -> string
