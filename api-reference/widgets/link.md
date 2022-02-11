# Link

This is used to create a link to another route or outside link.

### Example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Container(
            children=[
                Link("Go Home", to='/home'),
                Link("nicebookies.com/", to='https://nicebookies.com', external=True)
            ]
        )

runApp(App())
```

## Reference

### Properties

* textContent (positional) -> string
* to -> string link
* external -> boolean (default False) if true, link directly outside of the app.
* props -> dictionary of properties used to access HTML built-ins.
* className -> string
