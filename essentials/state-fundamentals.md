# State Fundamentals

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
            
            # A state change and the component UI haven't adapted to it
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

Every state must sit to the `__init__` method. This is because if you initialize a stateful variable to the `build` method, when the component rerenders, the variable is also reinitialize also to its default value.

## State class

You sometimes need a variable or a state to be shared between components, that's also possible with PyFyre.

```python
state = State({
    "count": 0
})
```

```python
return Text(state.count)
```

And you can create a new file for shared State among file components.

Similarly, if you just only want one state to be stored in a `State` class, you can just:

```python
state = State(0)

class App(UsesState):
    def build(self):
        return Text(state.value)
```

If you want to access them and change their values, you can just change them directly.

```python
state.count = state.count + 1
```

### Complete example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

state = State({
    "count": 0
})

class App(UsesState):
    def build(self):

        def increment(ev):
            state.count = state.count + 1
            self.update()

        return Container(
            children=[
                Text(state.count),
                Button("+", onClick=increment)
            ]
        )

runApp(App())
```
