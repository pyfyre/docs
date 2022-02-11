# Reactivity Fundamentals

`UsesState` provides a method called `update`, basically it rerenders the component as a whole, it deletes the component on the DOM and recreates it.&#x20;

Instead of rerendering the whole app when a state change, you'll have the power to just rerender the component only. When you call this, it will run the `build` method again and the component rerenders.

To use the API, you must call `self.update()` on a component that inherits the `UsesState` class.

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def __init__(self):
        self.text = "Click me!"

    def build(self):
        
        def change_text(ev):
            self.text = "You clicked me!"
            
            # A state change and the component UI hasn't adapt to it
            # yet, to rerender the component, you must call `self.update()`
            self.update()

        return Button(
            self.text,
            onClick=change_text
        )

runApp(
    App(),
    mount="app-mount"
)
```

Every state must sit to the `__init__` method. This is because if you initialize a stateful variable t the `build` method, when the component rerenders, the variable is also reinitialize also to its default value.
