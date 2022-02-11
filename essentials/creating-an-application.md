# Creating an Application

## The runApp method

Every PyFyre application starts to the class that inherits the `UsesState` class that's passed as the first parameter of the `runApp` method provided by PyFyre:

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Text("PyFyre App")

runApp(App()) # the apps starts with App class.
```

## Mounting the App

You can specify where you want your app mounts to the `index.html:`

{% code title="src/__init__.py" %}
```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        return Text("PyFyre App")

runApp(
    App(),
    mount="app-mount" # The id of the element
)
```
{% endcode %}

{% code title="index.html" %}
```html
<!DOCTYPE html>
<html lang="en">
    <body onload="brython()">
        <div id="app-mount">
            <!--The app mounts here-->
        </div>
    </body>
</html>
```
{% endcode %}

## UsesState class

To use PyFyre's API built-ins, you must inherit the `UsesState` class:

```python
class App(UsesState):
    def build(self):
        ...
```

It's just tells PyFyre that the component is a Stateful component. That means you expect the component to rerender several times.
