# Python Interview Preparation

## Day 3 – Functions and Variables

### 1. What is the difference between local and global variables in Python?

A **local variable** is defined inside a function and is normally available only within that function. A **global variable** is defined outside functions and can be read throughout the module.

To assign to a global variable from inside a function, declare it with `global`. Prefer returning a value or passing it as an argument when possible, since changing global state can make code harder to understand.

```python
count = 0  # global

def increment():
    global count
    count += 1
    message = "updated"  # local
    return message
```

### 2. What is the difference between positional, keyword, and default arguments?

- **Positional arguments** are matched to parameters by their order.
- **Keyword arguments** are matched by parameter name, so their order can vary.
- **Default arguments** have a value specified in the function definition; callers can omit them.

```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

greet("Mira")                   # positional; greeting uses its default
greet(name="Mira")              # keyword; greeting uses its default
greet("Mira", "Welcome")        # both positional
greet(greeting="Welcome", name="Mira")  # both keyword
```

Parameters without defaults must come before parameters with defaults.

### 3. `*args` and `**kwargs`: What are they, and when do we use them?

`*args` collects any extra positional arguments into a tuple. `**kwargs` collects any extra keyword arguments into a dictionary. They are useful when a function needs to accept a flexible number of arguments or pass arguments through to another function.

```python
def show_arguments(*args, **kwargs):
    print(args)
    print(kwargs)

show_arguments(1, 2, name="Mira")
# (1, 2)
# {'name': 'Mira'}
```

The names `args` and `kwargs` are conventions; the `*` and `**` syntax is what matters.

### 4. What is the difference between `return` and `print()` in Python?

`return` sends a value back to the code that called a function, where it can be stored or used in another expression. `print()` displays text in the console and does not send that displayed text back to the caller. A function without an explicit `return` returns `None`.

```python
def add(a, b):
    return a + b

result = add(2, 3)  # result is 5
print(result)       # displays 5
```

### 5. What is a lambda function in Python, and how is it different from a normal function?

A **lambda** is a small anonymous function written as a single expression. Its expression's value is returned automatically. A normal function, defined with `def`, can have a name and a multi-statement body, so it is generally better for reusable or more complex logic.

```python
double = lambda number: number * 2

def double_normal(number):
    return number * 2
```

Both calls, `double(4)` and `double_normal(4)`, return `8`. Lambdas are often used for short callbacks or sort keys; use `def` when the logic needs multiple steps or a descriptive docstring.
