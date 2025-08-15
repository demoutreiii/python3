# Built-in Constants


## \_\_debug\_\_

This constant is true if Python was not started with an [` -O `](<https://docs.python.org/3/using/cmdline.html#cmdoption-O>) option. See also the [` assert `](<https://docs.python.org/3/reference/simple_stmts.html#assert>) statement.

> Source: [` Built-in Constants | __debug__ `](<https://docs.python.org/3/library/constants.html#debug__>)


## Ellipsis

The same as the ellipsis literal "` ... `". Special value used mostly in conjunction with extended slicing syntax for user-defined container data types. ` Ellipsis ` is the sole instance of the [` types.EllipsisType `](<https://docs.python.org/3/library/types.html#types.EllipsisType>) type.

> Source: [` Built-in Constants | Ellipsis `](<https://docs.python.org/3/library/constants.html#Ellipsis>)


## False

The false value of the [` bool `](<https://docs.python.org/3/library/functions.html#bool>) type.

> Source: [` Built-in Constants | False `](<https://docs.python.org/3/library/constants.html#False>)


## None

An object frequently used to represent the absence of a value, as when default arguments are not passed to a function. ` None ` is the sole instance of the [` NoneType `](<https://docs.python.org/3/library/types.html#types.NoneType>) type.

> Source: [` Built-in Constants | None `](<https://docs.python.org/3/library/constants.html#None>)


## NotImplemented

A special value which should be returned by the binary special methods to indicate that the operation is not implemented with respect to the other type; may be returned by the in-place binary special methods for the same purpose. It should not be evaluated in a boolean context. ` NotImplemented ` is the sole instance of the [` types.NotImplementedType `](<https://docs.python.org/3/library/types.html#types.NotImplementedType>) type.

> Source: [` Built-in Constants | NotImplemented `](<https://docs.python.org/3/library/constants.html#NotImplemented>)

> [!CAUTION]
> ` NotImplemented ` and ` NotImplementedError ` are not interchangeable. This constant should only be used as described above; see [` NotImplementedError `](<https://docs.python.org/3/library/exceptions.html#NotImplementedError>) for details on correct usage of the exception.


## True

The true value of the [` bool `](<https://docs.python.org/3/library/functions.html#bool>) type.

> Source: [` Built-in Constants | True `](<https://docs.python.org/3/library/constants.html#True>)


## Constants added by the [` site `](<https://docs.python.org/3/library/site.html#module-site>) module

The [` site `](<https://docs.python.org/3/library/site.html#module-site>) module (which is imported automatically during startup, except if the [` -S `](<https://docs.python.org/3/using/cmdline.html#cmdoption-S>) command-line option is given) adds several constants to the built-in namespace. They are useful for the interactive interpreter shell and should not be used in programs.


### exit()
### quit()

Objects that when printed, print a message like "Use quit() or Ctrl-D (i.e. EOF) to exit", and when called, raise [` SystemExit `](<https://docs.python.org/3/library/exceptions.html#SystemExit>) with the specified exit code.

**Parameters**:
- **code**: Optional[` int `] - exit code. Defaults to ` None `.

> Source: [` Built-in Constants | exit() `](<https://docs.python.org/3/library/constants.html#exit>)
> Source: [` Built-in Constants | quit() `](<https://docs.python.org/3/library/constants.html#quit>)


### help

Object that when printed, prints the message "Type help() for interactive help, or help(object) for help about object.", and when called, acts as described [elsewhere](<https://docs.python.org/3/library/functions.html#help>).