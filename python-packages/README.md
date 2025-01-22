<h1>
  <span class="headline">Python Modules and Packages</span>
  <span class="subhead">Python Packages</span>
</h1>

**Learning objective:** By the end of this lesson, you will be able to **explain** the concept of Python packages and **demonstrate** their creation and usage, including the structure of package folders, the purpose of `__init__.py` files, and the process of importing modules from packages.

## Creating Packages

In Python, a **package** is a collection of **modules** organized into a folder. Packages help structure your codebase logically, especially in larger projects, by grouping related modules together. This makes your code easier to read, maintain, and reuse.

For example, you might have a package named `config` that groups modules related to configuration, such as one for handling conversions. With packages, you can use dot notation to access specific modules, keeping everything neatly organized.

## The Role of `__init__.py`

The `__init__.py` file is a special file in a package folder. It tells Python that the folder should be treated as a package. You can use it for initialization logic, such as automatically importing other modules within the package. If no special initialization is needed, the file can simply be left blank ([as long as you're running Python 3.3 or later](https://peps.python.org/pep-0420/)). Think of it like the `__init__()` method in a class—it sets up the package for use.

## Creating and using a package

We will create a package named `config` to organize our code. Follow these steps to set up the folder structure:

We want to create the following:

```bash
.
├── config
│   ├── converter.py
│   └── __init__.py
└── main.py
```

This structure organizes the `converter.py` module into the config package. The `__init__.py` file will mark the folder as a package.

### Create the `config` folder

This will serve as the package to hold your `converter.py` module:

```bash
mkdir config
```

Create an empty `__init__.py` file inside the config folder. This tells Python that `config` is a package:

```bash
touch config/__init__.py
```

Organize your code by moving `converter.py` into the `config` package:

```bash
mv converter.py config
```

Run the `tree` command or `ls -R` to confirm the structure:

```bash
.
├── config
│   ├── converter.py
│   └── __init__.py
└── main.py

1 directory, 3 files
```

Now that the `config` package is set up, you can import the `converter.py` module into your `main.py` file:

```py
from config import converter
```

Update the function call to reference the `converter` module explicitly:

```py
# old code 

result = convert(amount, unit)
```

To this:

```py
# new code 

result = converter.convert(amount, unit)
```

Run the program to ensure everything works correctly. By organizing your code into a package, you’ve made it more modular and maintainable!
