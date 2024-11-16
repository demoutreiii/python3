# Functions
Functions in Python are defined by the [` def `](https://github.com/demoutreiii/python3/blob/main/reserved_keywords.md#def) keyword, and is followed by the name of the function in snake_case.

Functions hold a block of code that can be repeatedly used by your script. To execute a function, type its name, followed by an open and closing parentheses. By default, functions return ` None ` when not explicitly specified in the callback code.

**Example**
```py
def hello_world():
  print("hello world")

text = hello_world()

>>> hello_world()
"hello world"

>>> text
None
```


## Function Arguments
Arguments what lets you pass values to the functions. These are defined inside the ` () ` parentheses in the function definition line. There are two types of arguments: **Positional argumemts**, and **Keyword arguments**.

### Positional Arguments
From the name itself, values are parsed to the function based on the position it is placed inside the parentheses.
```py
def add_numbers(x, y):
  print(f"{x = }")
  print(f"{y = }")
  return x + y

>>> add_numbers(2, 5)
"x = 2"
"y = 5"
7
```

### Keyword Arguments
Values are parsed based on its corresponding keyword in the function call.
```py
def add_numbers(x, y):
  print(f"{x = }")
  print(f"{y = }")
  return x + y

>>> add_numbers(y = 2, x = 5)
"x = 5"
"y = 2"
7
```

### Default Argument Values
Arguments can be set with a default value. When done, these arguments should be placed last, or after those arguments that doesn't have a default value and are positional. When a default value is placed, the argument becomes optional to be passed during function call. Function arguments default to being required to be passed, otherwise will raise an exception.
```py
def add_numbers(x, y = 5):
  print(f"{x = }")
  print(f"{y = }")
  return x + y

>>> add_numbers(2)
"x = 2"
"y = 5"
7

>>> add_numbers()
Exception: argument x is required
```

### Asterisk and Slash Arguments
` * ` and ` / ` can be set as arguments. These wildcard arguments define whether the arguments can be passed as positional or keyword, positional-only, or keyword-only arguments.

|         Left Side               | Divider |           Right Side            |
|---------------------------------|---------|---------------------------------|
|    Positional-only arguments    |    /    | Positional or keyword arguments |
| Positional or keyword arguments |    *    |      keyword-only arguments     |

```py
def greet(name : str, *, time : str) -> NoReturn:
  greetings : Dict[str, str] = {
    "day"   : "Good morning",
    "night" : "Good evening"
  }
  greeting : Optional[str] = greetings.get(time.lower())
  if greeting:
    print(f"{greeting}, {name}")
  else:
    raise Exception("time must either be 'day' or 'night'")

>>> greet("demo", time = "day")
"Good morning, demo"

>>> greet("demo", "day")
TypeError: greet() got some keyword-only arguments passed as positional arguments: 'time'
```


## Decorators
Functions can be attached to another function or class using the ` @ ` symbol followed by the function name, these functions called decorators. Top-level functions are the simplest form of decorators. Top-level function decorators require 1 argument: ` function ` - the function the decorator is attached to.
```py
def wrapper(function : Union[Callable[[...], ...], Awaitable]) -> NoReturn:
  print("hello world")

>>> @wrapper
... def sample() -> NoReturn: ...
"hello world"
```

### Decorator Arguments

Decorator functions may also accept other arguments which are passed during the decorator attachment. This is applicable in a nested function.
```py
def add_numbers(x : Union[int, float], y : Union[int, float]) -> NoReturn:
  def wrapper(function : Callable[[...], ...]) -> NoReturn:
    print(f"{x + y = }")
  return wrapper

>>> @add_numbers(2, 3)
... def sample() -> NoReturn: ...
"2 + 3 = 5"
```

### Decorator Return Values

By default, functions return ` None ` when not explicitly specified in the function callback. Thus, in the two examples above, ` sample ` function will become ` NoneType `.
```py
@wrapper
def sample() -> NoReturn: ...

>>> sample()
TypeError: 'NoneType' object is not callable

>>> type(sample)
<class NoneType>
```

To fix this, a ` return ` value is placed inside the ` wrapper ` function.
```py
def wrapper(function : Union[Callable[[...], ...], Awaitable]) -> datetime:
  return datetime.now()

@wrapper
def sample() -> NoReturn: ...

>>> type(sample)
<class datetime.datetime>
```

> **See Also**
> 
> - [Function Return Annotations](https://github.com/demoutreiii/python3/blob/main/type_annotations.md#return-annotations)