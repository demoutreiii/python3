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
> Source: [` abs() `](<https://docs.python.org/3/library/functions.html#abs>)


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
> Source: [` aiter() `](<https://docs.python.org/3/library/functions.html#aiter>)


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

> Source: [` all() `](<https://docs.python.org/3/library/functions.html#all>)


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
> Source: [` awaitable anext() `](<https://docs.python.org/3/library/functions.html#anext>)


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

> Source: [` any() `](<https://docs.python.org/3/library/functions.html#any>)


### ascii()
As [` repr() `](<https://docs.python.org/3/library/functions.html#repr>), return a string containing a printable representation of an object, but escape the non-ASCII characters in the string returned by the [` repr() `](<https://docs.python.org/3/library/functions.html#repr>).

**Parameters**:
- **object**: ` Object `

**Returns**: ` str `

> Source: [` ascii() `](<https://docs.python.org/3/library/functions.html#ascii>)


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

> Source: [` bin() `](<https://docs.python.org/3/library/functions.html#bin>)


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

> Source: [` bool() `](<https://docs.python.org/3/library/functions.html#bool>)