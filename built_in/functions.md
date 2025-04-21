## Built-In Functions


### abs()
Return the absolute value of an integer, floating-point, or an object implementing ` __abs__() `. If the argument is a complex number, its magnitude is returned.

**Parameters**:
- **x** - variable to get the absolute value of.

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
- **async_iterable** - asynchronous iterable to return its asynchronous iterator of

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