---
description: Welcome to PyFyre documentation!
---

# Introduction

## What is PyFyre?

PyFyre is a web frontend framework for building reactive static user interfaces on the web using only using Python.

* **Component-based framework.** Developers who have experience of using other frontend frameworks should feel quite at home when using PyFyre, especially Flutter developers.
* **Supports CPython interoperability.** Allowing developers to use existing PyPi packages on the client-side web (Still Experimental)
* **Reactive.** PyFyre automatically tracks Python state changes and efficiently updates the DOM when changes happen - as fast as vanilla JavaScript.

Here's a simple example:

```python
from pyfyre.widgets import *
from pyfyre.pyfyre import runApp

class MyWebpage(UsesState):
    def __init__(self):
        self.count = 0

    def build(self):
        
        def increment(ev):
            self.count = self.count + 1
            self.update() # Rerenders the component

        return Container(
            children=[
                Button(f"Count is: {self.count}", onClick=increment)
            ]
        )

runApp(MyWebpage())
```

The full tutorial with explanation of this example can be found [here](samples-and-tutorials/cookbook/create-a-counter-app.md)

## Join us!

* You can report bugs and discuss features on our [GitHub Issues Page](https://github.com/pyfyre/pyfyre/issues)
* Want to support the development of PyFyre and help us make it more better? Make pull requests if you'd like to help out!

## Want to jump right in?

Feeling like an eager beaver? Jump in to the quick start docs:

{% content-ref url="quick-start.md" %}
[quick-start.md](quick-start.md)
{% endcontent-ref %}

## Still not convinced?

We know that you're pretty new to Python on the client-side web. This project is built at the top of [Brython](https://brython.info) (Browser Python), a Python implementation for client-side web programming.

### But why Brython?

Brython is fast and provides an API to JavaScript. It allows PyFyre to communicate with JavaScript and use its APIs, manipulate the DOM, and actually everything you can do with JavaScript is also possible with Brython. Brython's speed of execution is still similar to CPython for most of its operations.&#x20;

If you want to deep dive about how Brython works under the hood, you might want to check this out: [https://github.com/brython-dev/brython/wiki/How-Brython-works](https://github.com/brython-dev/brython/wiki/How-Brython-works)

### Okay... but why?

There's already a lot of front-end frameworks created by the tech giants. PyFyre is not going to compete with those giants, instead, PyFyre will be targeting a different niche in the developer community.&#x20;

PyFyre's goal is to:

* Simplify web development. Avoid Jargons that really don't even make sense. Makes it easy to create a reactive single-page web applications using a beginner-friendly language, Python.
* Allows the client-side web to access CPython's packages and Built-ins that's really tiny for the client (even it's a Phone) to handle Python's operations.
* And also to use NPM packages at the same time along with CPython's packages.
