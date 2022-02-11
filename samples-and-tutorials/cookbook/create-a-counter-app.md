# Create a Counter app

This recipe covers how to create a reactive counter app with PyFyre.

This recipe uses the following steps:

1. Create a new component
2. Initialize the `count` variable on the `__init__` method.
3. Create a Button widget.
4. Create an `increment` method.

### 1. Create a new component

To create a component, you need to create a new class inheriting the `UsesState` class from PyFyre widgets. This allows us to leverage PyFyre's built-ins to our class and access its properties, methods, and attributes. &#x20;

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class CounterApp(UsesState):
    def build(self):
        pass
        
runApp(CounterApp()) # Where your app's starts to render.
```

We need to override the build method of the `UsesState` class and return our widget we want to render on the screen.

Now we're going to add a Container as the parent of our widgets.

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class CounterApp(UsesState):
    def build(self):
        return Container(
            children=[
            ]
        )
```

### 2. Initialize the \`count\` variable on the \_\_init\_\_ method.

```python
class MyWebpage(UsesState):
    def __init__(self):
        self.count = 0
```

Now you might ask, why on the `__init__` method of the class? Well, `__init__` methods are called when the class is called for the first time, in other languages, it's the constructor. `__init__` methods are not called when the component rerenders unless the parent component of the component rerenders.

If we initialize our `count` variable to our `build` method. It's going to be initialize again to its initial value when the component rerenders. Because remember, when a component rerenders when a state change, the `build` method will be called again and in that case, count will be `0` again.

### 3. Create a Button widget

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class CounterApp(UsesState):
    def build(self):
        return Container(
            children=[
               Button(f"Count is: {self.count}")
            ]
        )
```

Now, we're going to create a button widget and interpolate our `count` variable.

### 4. Create an \`increment\` method

Button also needs another parameter called `onClick`, it's a method you pass that when a user clicks to that button, the method you passed is called automatically giving you an argument called `event` used to access JavaScript's `preventDefault` function or others.

```python
def build(self):

    def increment(ev):
        self.count = self.count + 1
        self.update() # Rerenders the component
    
    return Container(
        children=[
           Button(f"Count is: {self.count}", onClick=increment)
        ]
    )
```

As you can see, we wrapped the `increment` method to our `build` method. This is optional.

Alternatively, you can declare your method on the class itself:

```python
class MyWebpage(UsesState):
    def __init__(self):
        self.count = 0

    def increment(self, ev):
        self.count = self.count + 1
        self.update() # Rerenders the component

    def build(self):
        return Container(
            children=[
                Button(f"Count is: {self.count}", onClick=self.increment)
            ]
        )
```

And voila! You now have a running counter app created with PyFyre!

## Complete example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class MyWebpage(UsesState):
    def __init__(self):
        self.count = 0

    def increment(self, ev):
        self.count = self.count + 1
        self.update() # Updates the component

    def build(self):
        return Container(
            children=[
                Button(f"Count is: {self.count}", onClick=self.increment)
            ]
        )

runApp(MyWebpage())
```
