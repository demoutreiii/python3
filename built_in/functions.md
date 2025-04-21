## Built-In Functions


### abs()
Return the absolute value of an integer, floating-point, or an object implementing ` __abs__() `. If the argument is a complex number, its magnitude is returned.

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
Return an asynchronous iterator for an asynchronous iterable. Equivalent to calling ` x.__aiter__() `.

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
When awaited, return the next item from the asynchronous iterator, or ` default ` if given and the iterator is exhausted.

This calls the ` __anext__() ` method of the ` async_iterator `, returning an awaitable. Awaiting this returns the next value of the iterabor. If ` default ` is given, it is returned if the iterator is exhausted, otherwise ` StopAsyncIteration ` is raised.

**Parameters**:
- **async_iterator**: ` AsyncIterable ` - asynchronous iterator
- **default**: ` Optional[Any] ` - default value to return if the iterator is exhausted

> Added in version 3.10
> Source: [` awaitable anext() `](<https://docs.python.org/3/library/functions.html#anext>)