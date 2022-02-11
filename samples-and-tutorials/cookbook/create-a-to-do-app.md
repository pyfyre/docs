# Create a To-Do app

Of course, we want to keep track of what have we already done and what needs to be done. In this recipe, we will cover on how to create a simple To-Do app with PyFyre.

This recipe uses the following steps:

1. Initialize the TextInputController
2. Create the TextInput widget.
3. Create the `add_todo` method.
4. Create an Add To-Do button.
5. Create the To-Do list.
6. Create the `todos_list` method.

### 1. Initialize the TextInputController

TextInputControllers are used to leverage HTML built-ins on PyFyre, access its values and attributes.

You must initialize TextInputController on the `__init__` method.

```python
class ToDoApp(UsesState):
    def __init__(self):
        self.controller = TextInputController()
```

And also add our `todos` variable that is an array of strings where we're going to store all the To-Dos in-memory.

```python
class App(UsesState):
    def __init__(self):
        self.todos = []
        self.controller = TextInputController()
```

### 2. Create the TextInput widget.

```python
class App(UsesState):
    def __init__(self):
        self.todos = []
        self.controller = TextInputController()

    def build(self):
        return Container(
            children=[
                TextInput(
                    controller=self.controller
                ),
            ]
        )
```

Now we provide the controller to this `TextInput` so we can control it inside our code.

### 3. Create the \`add\_todo\` method.

Now, we're going to create a method to add a new To-Do.

```python
def add_todo(event):
    # We check if the current value of the TextInput has no value
    if len(self.controller.value) == 0: return
    
    # Append the value to the `todos` array.
    self.todos.append(self.controller.value)
    
    # Reset the value
    self.controller.setValue("")
    
    # Rerender the app
    self.update()
```

### 4. Create an Add To-Do button

```python
def build(self):
    return Container(
        children=[
            TextInput(
                controller=self.controller
            ),
            Button(
                "Add Todo",
                onClick=add_todo
            )
        ]
    )
```

### 5.  Create the To-Do list

```python
def build(self):
    return Container(
        children=[
            ListBuilder(
            
                # Provide the length of the To-Dos
                # `count` means, how many times will
                # the builder that we passed will run.
                count=len(self.todos),
                builder=...
            ),
            TextInput(
                controller=self.controller
            ),
        ]
    )
```

### 6. Create the \`todos\_list\` method

Now, we're going to create the `todos_list` method and pass it to the `builder` on the ListBuilder on our UI.

```python
def todos_list(i):

    def finish_todo(e):
        del self.todos[i]
        self.update()
    
    # Builder requires a Widget to render
    return Container(
        props={"style": "display: flex;"},
        children=[
            Text(self.todos[i]),
            Button("Finish", onClick=finish_todo)
        ]
    )
```

The `i` is the index count of the builder that we're going to use to map through the `todos` variable.

## Complete example

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def __init__(self):
        self.todos = []
        self.controller = TextInputController()

    def build(self):

        def todos_list(i):

            def finish_todo(e):
                del self.todos[i]
                self.update()

            return Container(
                props={"style": "display: flex;"},
                children=[
                    Text(self.todos[i]),
                    Button("Finish", onClick=finish_todo)
                ]
            )

        def add_todo(e):
            if len(self.controller.value) == 0: return

            self.todos.append(self.controller.value)
            self.controller.setValue("")
            self.update()

        return Container(
            children=[
                ListBuilder(
                    count=len(self.todos),
                    builder=todos_list
                ),
                TextInput(
                    controller=self.controller
                ),
                Button(
                    "Add Todo",
                    onClick=add_todo
                )
            ]
        )

runApp(
    App(),
    mount="app-mount"
)
```
