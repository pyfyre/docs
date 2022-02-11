# Error Handling

## PyFyre Error Barrier

PyFyre has an error handling feature that you are going to love - inspired by Remix Error Boundary. Handle errors on every component separately. When an error interrupts the `build` method on the component, the`onerror` method will be called and you can handle it professionally without blowing the entire app. Override the `onerror` method by declaring another `onerror` method to your component and taking another parameter where the error exception will pass. You can return a widget in which the UI you want your users to see temporarily.

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class App(UsesState):
    def build(self):
        None in 5 # Produces TypeError

        return Text("Hello, my awesome app!")

    def onerror(self, error):
        return Text("Oops! Something went wrong.")

runApp(
    App(),
    mount="app-mount"
)
```

![Error Barrier example](../.gitbook/assets/image.png)
