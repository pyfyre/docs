---
description: Get started with PyFyre in this documentation
---

# Quick Start

### Prerequisites

* Python 3.x
* A working environment

To install PyFyre, you need to install Python 3.x, and a working `pip` command.

To make sure you installed it correctly, go to your terminal (cmd on Windows) and type `py --version` if Python version shows, you already have Python. To check `pip`, type `pip --version` and it should show as well.

### Install PyFyre CLI

You need PyFyre CLI to create projects, generate application and perform commands.

To install the PyFyre CLI, open a terminal window (cmd on Windows) and run the following command:

```bash
pip install pyfyre
```

### Create an App

Start your app and create a new workspace to develop your apps.

To create a new app, run the PyFyre CLI command:

```
pyfyre create my-cool-app
```

You can replace \`my-cool-app\` with the name of the app you desired.

### Run the App

PyFyre has a development server with a hot reload that detects changes in your code and reload the application automatically.

1. Navigate to the app folder, in our case, it's `my-cool-app`
2. Run PyFyre CLI command:

```
pyfyre run
```

And voila! You now have a running PyFyre app on your local machine.

_Note: Once you have run the app, PyFyre will generate a folder called_ `_pyfyre`_, the folder contains all the files the running server need. You can delete it once_ `run` _has finished._
