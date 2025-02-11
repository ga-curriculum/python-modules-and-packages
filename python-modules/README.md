<h1>
  <span class="headline">Python Modules and Packages</span>
  <span class="subhead">Python Modules</span>
</h1>

**Learning objective:** By the end of this lesson, you will be able to **understand** how Python modules can be used to organize code effectively, and **demonstrate** module importing syntax.

When structuring our code, each new file becomes a _module_ which allows us to organize our code more effectively.

Let's practice creating and using a module. We want to create a converter module, which converts imperial to metric. We create a `converter.py` where our converter logic will live, and a `main.py` file where we will import our converter to be used in the main business logic:

Let's create a new file called `converter.py`:

```sh
touch converter.py
```

In your code editor, add the following to `converter.py`:

```py
# converter.py

ratios = {
  'lbs': 0.453592,
  'stone': 6.35029,
  'fl oz': 28.4131,
  'pint': 568.261
}

def convert(amount, unit):
  return amount * ratios.get(unit, 1)
```

Save the file in the directory you just created.

Next, create the `main.py`

```sh
touch main.py
```

And add the following:

```py
# main.py

import converter  # converter module loaded into memory

unit = input("What do you want to convert? lbs / stone / fl oz / pint ")
amount = float(input(f"How many {unit} to convert? "))
result = converter.convert(amount, unit)
metric = "kg" if unit in ["lbs", "stone"] else "ml"

print(f"{amount} {unit} is {result} {metric}")
```

Let's test and make sure the program works.

```sh
python3 main.py
```

Here we have imported the whole `converter` module, including the `ratios` dictionary. This is actually not necessary since we do not use `ratios` in the `main.py` file.

Instead we can just import the `convert` method like so:

```py
# main.py

from converter import convert  # <--- Change this line

unit = input("What do you want to convert? lbs / stone / fl oz / pint ")
amount = float(input(f"How many {unit}s to convert? "))
result = convert(amount, unit)  # <--- And this line
print(result)
```

Run the program again and verify it works the same.
