## Built-In Functions


### abs()
Return the absolute value of an integer, floating-point, or an object implementing [` __abs__() `](<https://docs.python.org/3/reference/datamodel.html#object.__abs__>). If the argument is a complex number, its magnitude is returned.

**Parameters**:
- **x**: ` Union[int, float, Object] ` - variable to get the absolute value of.

**Returns**: ` Union[int, float, Any] `

```py
>>> number: int = 123
>>> abs(number)
123
>>> number:int = -123
>>> abs(number)
123
```
> Source: [` Built-in Functions | abs() `](<https://docs.python.org/3/library/functions.html#abs>)


### aiter()
Return an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator) for an [asynchronous iterable](https://docs.python.org/3/glossary.html#term-asynchronous-iterable). Equivalent to calling ` x.__aiter__() `.

**Parameters**:
- **async_iterable**: ` AsyncIterable ` - asynchronous iterable to return its asynchronous iterator of

**Returns**: asynchronous iterator

```py
class A:
  async def __aiter__(self) -> int:
    for i in range(5):
      yield i

async def sample() -> None:
  async for i in A():
    print(i)
```

> Added in version 3.10
> Source: [` Built-in Functions | aiter() `](<https://docs.python.org/3/library/functions.html#aiter>)


### all()
Return ` True ` if all of the elements in the iterable are true (or if the iterable is empty).

**Parameters**:
- **iterable**: ` Iterable ` - the iterable to check for

**Returns**: ` bool `

```py
>>> all([False, False])
False
>>> all([True, False])
False
>>> all([True, True])
True
>>> all([])
True
```

> Source: [` Built-in Functions | all() `](<https://docs.python.org/3/library/functions.html#all>)


### anext()
When awaited, return the next item from the given [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator), or ` default ` if given and the iterator is exhausted.

This calls the [` __anext__() `](https://docs.python.org/3/reference/datamodel.html#object.__anext__) method of the ` async_iterator `, returning an [awaitable](https://docs.python.org/3/glossary.html#term-awaitable). Awaiting this returns the next value of the iterabor. If ` default ` is given, it is returned if the iterator is exhausted, otherwise [` StopAsyncIteration `](https://docs.python.org/3/library/exceptions.html#StopAsyncIteration) is raised.

**Parameters**:
- **async_iterator**: ` AsyncIterable ` - asynchronous iterator
- **default**: ` Optional[Any] ` - default value to return if the iterator is exhausted

**Returns**: ` Any `

**Raises**:
- **StopAsyncIteration** - iterator is exhausted and ` default ` is not provided

> Added in version 3.10
> Source: [` Built-in Functions | anext() `](<https://docs.python.org/3/library/functions.html#anext>)


### any()
Return ` True ` if any element in the ` iterable ` is true. If the iterable is empty, returns ` False `.

**Parameters**:
- **iterable**: ` Iterable `

**Returns**: ` bool `

```py
>>> any([False, False])
False
>>> any([True, False])
True
>>> any([True, True])
True
>>> any([])
False
```

> Source: [` Built-in Functions | any() `](<https://docs.python.org/3/library/functions.html#any>)


### ascii()
As [` repr() `](<https://docs.python.org/3/library/functions.html#repr>), return a string containing a printable representation of an object, but escape the non-ASCII characters in the string returned by the [` repr() `](<https://docs.python.org/3/library/functions.html#repr>).

**Parameters**:
- **object**: ` Object `

**Returns**: ` str `

> Source: [` Built-in Functions | ascii() `](<https://docs.python.org/3/library/functions.html#ascii>)


### bin()
Convert an integer number to a binary string prefixed with "0b". If ` number ` is not a Python [` int `](<https://docs.python.org/3/library/functions.html#int>) object, it has to define an [` __index__() `](<https://docs.python.org/3/reference/datamodel.html#object.__index__>) method that returns an integer.

**Parameters**:
- **number**: ` Union[int, Object] `

**Returns**: ` str `

```py
>>> bin(3)
'0b11'
>>> bin(-10)
'0b1010'
```

If the prefix "0b" is desired or not, you can use either of the following ways:

```py
>>> format(14, "#b"), format(14, "b")
("0b1110", "1110")
>>> f"{14:#b}", f"{14:b}"
("0b1110", "1110")
```

> Source: [` Built-in Functions | bin() `](<https://docs.python.org/3/library/functions.html#bin>)


### bool()
Return a Boolean value, i.e. one of ` True ` or ` False `. The argument is converted using the standard [truth testing procedure](<https://docs.python.org/3/library/stdtypes.html#truth>). If the argument is false or omitted, this returns ` False `; otherwise it returns ` True `. The [` bool `](<https://docs.python.org/3/library/functions.html#bool>) class is a subclass of [` int `](<https://docs.python.org/3/library/functions.html#int>). It cannot be subclassed further.

**Parameters**:
- **object**: ` Optional[bool] `

**Returns**: ` bool ` - defaults to ` False `

```py
>>> bool(0)
False
>>> bool(1)
True
>>> bool("")
False
>>> bool("python")
True
```

> Source: [` Built-in Functions | bool() `](<https://docs.python.org/3/library/functions.html#bool>)


### breakpoint()
This function drops you into the debugger at the call site. Specifically, it calls [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>), passing ` args ` and ` kwargs ` straight through. By default, ` sys.breakpointhook() ` calls [` pdb.set_trace() `](<https://docs.python.org/3/library/pdb.html#pdb.set_trace>) expecting no arguments. In this case, it is purely a convenience function so you don't have to explicitly import [` pdf `](<https://docs.python.org/3/library/pdb.html#module-pdb>) or type as much code to enter the debugger. However, [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>) can be set to some other function and [` breakpoint() `](<https://docs.python.org/3/library/functions.html#breakpoint>) will automatically call that, allowing you to drop into the debugger of choice. If [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>) is not accessible, this function will raise [` RuntimeError `](<https://docs.python.org/3/library/exceptions.html#RuntimeError>).

By default, the behavior of [` breakpoint() `](<https://docs.python.org/3/library/functions.html#breakpoint>) can be changed with the [` PYTHONBREAKPOINT `](<https://docs.python.org/3/using/cmdline.html#envvar-PYTHONBREAKPOINT>) environment variable. See [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>) for usage details.

Note that this is not guaranteed if [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>) has been replaced.

Raises an [auditing event](<https://docs.python.org/3/library/sys.html#auditing>) ` builtins.breakpoint ` with argument ` breakpointhook `.

**Parameters**:
- **args** - positional arguments
- **kwargs** - keyword-arguments

**Raises**:
- [**RuntimeError**](<https://docs.python.org/3/library/exceptions.html#RuntimeError>) - [` sys.breakpointhook() `](<https://docs.python.org/3/library/sys.html#sys.breakpointhook>) is not accessible.

> Source: [` Built-in Functions | breakpoint() `](<https://docs.python.org/3/library/functions.html#breakpoint>)


### bytearray()
Return a new array of bytes. The [` bytearray `](<https://docs.python.org/3/library/stdtypes.html#bytearray>) class is a mutable sequence of integers in the range ` 0 <= x < 256 `. It has most of the usual methods of mutable sequences, described in [Mutable Sequence Types](<https://docs.python.org/3/library/stdtypes.html#typesseq-mutable>), as well as most methods that the [` bytes `](<https://docs.python.org/3/library/stdtypes.html#bytes>) type has, see [Bytes and Bytesarray Operations](<https://docs.python.org/3/library/stdtypes.html#bytes-methods>).

The optional ` source ` parameter can be used to initialize the array in a few different ways:

 - If it is a string, you must also give the ` encoding ` (and optionally, ` errors `) parameters; [` bytearray() `](<https://docs.python.org/3/library/stdtypes.html#bytearray>) then converts the string to bytes using ` str.encode() `](<https://docs.python.org/3/library/stdtypes.html#str.encode>).

 - If it is an integer, the array will have that size and will be initialized with null bytes.

 - If it is an object conforming to the [buffer interface](<https://docs.python.org/3/c-api/buffer.html#bufferobjects>), a read-only buffer of the object will be used to initialize the bytes array.

 - If it is an iterable, it must be an iterable of integers in the range ` 0 <= x < 256 `, which are used as the initial contents of the array.

 Without an argument, an array of size 0 is created.

 **Parameters**:
 - **source**: ` Optional[Union[str, int, Object, Iterable]] ` - defaults to an array with size of 0
 - **encoding**: ` Optional `
 - **errors**: ` Optional `

 **Returns**: ` bytearray `

 > Source: [` Built-in Functions | bytearray() `](<https://docs.python.org/3/library/stdtypes.html#bytearray>)


 ### callable()
 Return ` True ` if the ` object ` argument appears callable, ` False ` if not. If this returns ` True `, it is still possible that a call fails, but if it is ` False `, calling ` object ` will never succeed. Note that classes are callable (calling a class returns a new instance); instances are callable if their class has a [` __call__() `](<https://docs.python.org/3/reference/datamodel.html#object.__call__>) method.

 **Parameters**:
- **object**: ` Object `

**Returns**: ` bool `

> Source: [` Built-in Functions | callable() `](<https://docs.python.org/3/library/functions.html#callable>)


### chr()
Return the string representing a character whose Unicode code point is the integer ` i `. For example, ` chr(97) ` returns the string ` 'a' `, while ` chr(8364) ` returns the string ` '€' `. This is the inverse of [` ord `](<https://docs.python.org/3/library/functions.html#ord>).

The valid range for the argument is from 0 through 1,114,111 (0x10FFFF in base 16). [` ValueError `](<https://docs.python.org/3/library/exceptions.html#ValueError>) will be raised if ` i ` is out of range.

**Parameters**:
- **i**: ` int `

**Raises**:
- [**ValueError**](<https://docs.python.org/3/library/exceptions.html#ValueError>) - ` i ` is out of range

**Returns**: ` str `- Unicode code point string representation of the integer ` i `

> Source: [` Built-in Functions | chr() `](<https://docs.python.org/3/library/functions.html#chr>)


### complex()
Convert a single string or number to a complex number, or create a complex number from real and imaginary parts.

**Parameters**:
- **real**: ` Union[float, str] `
- **imag**: ` Union[str] `

**Raises**
- [**ValueError**](<https://docs.python.org/3/library/exceptions.html#ValueError>) - invalid imaginary parts syntax.

> Source: [` Built-in Functions | complex() `](<https://docs.python.org/3/library/functions.html#complex>)

**Returns**: ` complex `


### delattr()
Delete the named attribute of the object, if it allows it.

` delattr(x, 'foo') ` is equivalent to ` del x.foo `.

**Parameters**:
- **object**: ` Object `
- **name**: ` str ` - name of the attribute.

> Source: [` Built-in Functions | delattr() `](<https://docs.python.org/3/library/functions.html#delattr>)


### dict()
Create a new dictionary.

**Parameters**:
- **\*\*kwargs** - keyword arguments. Additionally, you may provide a mapping or iterable as well.

**Returns**: ` dict `

> Source: [` Built-in Functions | dict() `](<https://docs.python.org/3/library/stdtypes.html#dict>)


### dir()
Without arguments, returns the list of names in the current local scope. With an argument, attempts to return a list of valid attributes for that object.

**Parameters**:
- **object**: ` Object `

*Returns**: List[` str `]

```py
>>> dir()
['__builtins__', '__name__']
>>> dir(print)
['__call__', '__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__', '__self__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__text_signature__']
```

> Source: [` Built-in Functions | dir() `](<https://docs.python.org/3/library/functions.html#dir>)


### divmod()
Take two (non-complex) numbers as arguments and return a pair of numbers consisting of their quotient and remainder when using integer division.

**Parameters**:
- **a**: Union[` int `, ` float `]
- **b**: Union[` int `, ` float `]

**Returns**: Tuple[Union[` int `, ` float `], Union[` int `, ` float `]]

```py
>>> divmod(6, 3)
(2, 0)
>>> divmod(6, 4)
(1, 2)
```

> Source: [` Built-in Functions | divmod() `](<https://docs.python.org/3/library/functions.html#divmod>)


### enumerate()
Returns an enumerate object; yielding a tuple containing a count (from ` start ` which defaults to ` 0 `) and the values obtained from iterating over ` iterable `.

**Parameters**:
- **iterable**: Iterable
- **start**: ` int ` = start of the count. Defaults to ` 0 `.

**Returns**: Tuple[` int `, ` Object `]

```py
>>> fruits: list[str] = ["apple", "orange", "banana"]
>>> for count, fruit in enumerate(fruits):
...   print(count, fruit)
...
0 apple
1 orange
2 banana
```

> Source: [` Built-in Functions | enumerate() `](<https://docs.python.org/3/library/functions.html#enumerate>)


### filter()
Construct an iterator from those elements of ` iterable ` for which ` function(element) ` is ` True `.

**Parameters**:
- **function**: Union[Callable[` Object `, ` bool `], ` None `] - If ` None `, the identity function is assumed, that is, all elements of ` iterable ` that are false are removed.
- **iterable**: Union[Sequence, Container, Iterator]

```py
>>> samples: list[Union[int, None]] = [1, None, 3, 4, None]
>>> filtered_samples: list[Union[int]] = [item for item in filter(None, samples)]
>>> filtered_samples
[1, 3, 4]
```

> Source: [` Built-in Functions | filter() `](<https://docs.python.org/3/library/functions.html#filter>)


### float()
Return a floating-point number constructed from a number or a string. If no argument is given, returns ` 0.0 `.

**Parameters**:
- **arg**: Optional[Union[` str `, ` int `, ` float `]]

**Returns**: ` float `

```py
>>> float()
0.0
>>> float(1)
1.0
>>> float("123")
123.0
>>> float(1.0)
1.0
```

> Source: [` Built-in Functions | float() `](<https://docs.python.org/3/library/functions.html#float>)


### frozenset()
Returns a new [` frozenset `](https://docs.python.org/3/library/stdtypes.html#frozenset) object, optionally with elements taken from ` iterable ` argument.

**Parameters**:
- **iterable**: Optional[Iterable]

**Returns**: [` frozenset `](https://docs.python.org/3/library/stdtypes.html#frozenset)

> Source: [` Built-in Functions | frozenset() `](<https://docs.python.org/3/library/stdtypes.html#frozenset>)


### getattr()
Return the value of the named attribute of ` object `.

` getattr(x, "foobar") ` is equivalent to ` x.foobar `.

**Parameters**:
- **object**: ` Object `
- **name**: ` str ` = name of the attribute
- **default**: Optional[Any] = what is returned if the ` name ` attribute doesn't exist in ` object `. If not provided, [` AttributeError `](https://docs.python.org/3/library/exceptions.html#AttributeError) is raised.

**Returns**: Any

**Raises**:
- [**AttributeError**](https://docs.python.org/3/library/exceptions.html#AttributeError) = There is no provided ` name ` attribute of the ` object `, and ` default ` is not provided.

```py
>>> class Sample:
...   number: int = 123
...
>>> sample = Sample()
>>> getattr(sample, number)
123
```

> Source: [` Built-in Functions | getattr() `](https://docs.python.org/3/library/functions.html#getattr)


### globals()
Return the dictionary implementing the current module namespace. For code within functions, this is set when the function is defined and remains the same regardless of where the function is called.

**Returns**: dict[` str `, Any]

> Source: [` Built-in Functions | globals() `](https://docs.python.org/3/library/functions.html#globals)


### hasattr()
Returns ` True ` if the string is the name of one of the object's attributes, otherwise ` False `. This is implemented by calling ` getattr(object, name) ` and seeing whether it raises an [` AttributeError `](https://docs.python.org/3/library/exceptions.html#AttributeError) or not.

**Parameters**:
- **object**: ` Object `
- **name**: ` str `

```py
>>> class Sample:
...   text: str = "hello world"
...
>>> sample = Sample()
>>> getattr(sample, "text)
hello world
>>> hasattr(sample, "number")
False
>>> hasattr(sample, "text")
True
```

> Source: [` Built-in Functions | hasattr() `](https://docs.python.org/3/library/functions.html#hasattr)


### hash()
Returns the hash value of ` object ` (if it has one).

**Parameters**:
- **object**: ` Object `

**Returns**: Optional[` int `]

> Source: [` Built-in Functions | hash() `](<https://docs.python.org/3/library/functions.html#hash>)


### help()
Invokes the built-in help system.

If no argument is given, the interactive help system starts on the interpreter console. If the argument is a string, then the string is looked up as the name of a module, function, class, method, keyword, or documentation topic, and a help page is printed on the console. If the argument is any other kind of object, a help page on the object is generated.

This function is added to the built-in namespace by the [` site `](https://docs.python.org/3/library/site.html#module-site) module.

**Parameters**:
- **request**: Optional[Union[` str `, Any]]

!!! NOTE **NOTE**: This function is intended for interactive use.

> Source: [` Built-in Functions | help() `](<https://docs.python.org/3/library/functions.html#help>)


### hex()
Convert an integer number to a lowercase hexadecimal string prefixed with "0x". If ` x ` is not a Python [` int `](https://docs.python.org/3/library/functions.html#int) object, it has to define an [` __index__() `](https://docs.python.org/3/reference/datamodel.html#object.__index__) that returns an integer.

**Parameters**:
- **x**: Union[` int `, ` Object `]

**Returns**: ` str `

!!! NOTE **Note**: To obtain a hexadecimal string representation of a float, use the [` float.hex() `](https://docs.python.org/3/library/stdtypes.html#float.hex) method.

> Source: [` Built-in Functions | hex() `](https://docs.python.org/3/library/functions.html#hex)


### id()
Returns the "identity" of an object. This is an integer which is guaranteed to be unique and constant for this object during its lifetime. Two objects with non-overlapping lifetimes may have the same [` id() `](https://docs.python.org/3/library/functions.html#id) value.

**CPython implementation detail**: This is the address of the object in memory.

Raises an [auditing event](https://docs.python.org/3/library/sys.html#auditing) ` builtins.id ` with argument ` id `.

**Parameters**:
- **object**: ` Object `

**Returns**: ` int `

> Source: [` Built-in Functions | id() `](https://docs.python.org/3/library/functions.html#id)