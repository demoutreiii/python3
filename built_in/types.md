# Built-in Types


## Table of Contents
- [Truth Value Testing](<#truth-value-testing>)
- [Boolean Operations](<#boolean-operations>)


## Truth Value Testing

Any object that can be tested for truth value, for use in an [` if `](<https://docs.python.org/3/reference/compound_stmts.html#if>) or [` while `](<https://docs.python.org/3/reference/compound_stmts.html#while>) statement condition or as operated of the Boolean operations below.

By default, an object is considered true unless its class defines either a [` __bool__() `](<https://docs.python.org/3/reference/datamodel.html#object.__bool__>) method that returns ` False ` or a [` __len__() `](<https://docs.python.org/3/reference/datamodel.html#object.__len__>) method that returns zero, when called with the object. Here are most of the built-in objects considered false:
- constants defined to be false: ` None ` and ` False `
- zero of any numeric type: ` 0 `, ` 0.0 `, ` 0j `, ` Decimal(0) `, ` Fraction(0, 1) `
- empty sequences and collections: ` '' `, ` () `, ` [] `, ` {} `, ` set() `, ` range(0) `

> Source: [` Built-in Types | Truth Value Testing `](<https://docs.python.org/3/library/stdtypes.html#truth-value-testing>)


## Boolean Operations

These are the Boolean operations, ordered by ascending priority:

| Operation   | Result                                           | Notes |
|-------------|--------------------------------------------------|-------|
| ` x or y `  | if ` x ` is true, then ` x `, else ` y `         | (1)   |
| ` x and y ` | if ` x ` is false, then ` x `, else ` y `        | (2)   |
| ` not x `   | if ` x ` is false, then ` True `, else ` False ` | (3)   |

Notes:
1. This is a short-circuit operator, so it only evalues the second argument if the first one is false.
2. This is a short-circuit operator, so it only evaluates the second argument if the first one is true.
3. ` not ` has a lower priority than non-Boolean operators, so ` not a == b ` is interpreted as ` not (a == b) `, and ` a == not b ` is a syntax error.

> Source: [` Built-in Types | Boolean Operations `](<https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not>)


## Comparisons

There are eight comparison operations in Python. They all have the same priority (which is higher than that of the Boolean operations). Comparisons can be chained arbitrarily; for example, ` x < y <= x ` is equivalent to ` x < y and y <= z `, except that ` y ` is evaluated only once (but in both cases ` z ` is not evaluated at all when ` x < y ` is found to be false).

This table summarizes the comparison operations:

| Operation  | Meaning                 |
|------------|-------------------------|
| ` < `      | strictly less than      |
| ` <= `     | less than or equal      |
| ` > `      | strictly greater than   |
| ` >= `     | greater than or equal   |
| ` == `     | equal                   |
| ` != `     | not equal               |
| ` is `     | object identity         |
| ` is not ` | negated object identity |

Objects of different types, except different numeric types, never compare equal. The ` == ` operator is always defined but for some object types is equivalent to [` is `](<https://docs.python.org/3/reference/expressions.html#is>). The ` < `, ` <= `, ` > ` and ` >= ` operators are only defined where they make sense; for example, they raise a [` TypeError `](<https://docs.python.org/3/library/exceptions.html#TypeError>) exception when one of the arguments is a complex number.

Non-identical instances of a class normally compare as non-equal unless the class defines the [` __eq__() `](<https://docs.python.org/3/reference/datamodel.html#object.__eq__>) method.

Instances of a class cannot be ordered with respect to other instances of the same class, or other types of object, unless the calss defines enough of the methods [` __lt__() `](<https://docs.python.org/3/reference/datamodel.html#object.__lt__>), [` __le__() `](<https://docs.python.org/3/reference/datamodel.html#object.__le__>), [` __gt__() `](<https://docs.python.org/3/reference/datamodel.html#object.__gt__>), and [` __ge__() `](<https://docs.python.org/3/reference/datamodel.html#object.__ge__>).

The behavior of the [` is `](<https://docs.python.org/3/reference/expressions.html#is>) and [` is not `](<https://docs.python.org/3/reference/expressions.html#is-not>) operators cannot be customized; also they can be applied to any two objects and never raise an exception.

Two more operations with the same syntactic priority, [` in `](<https://docs.python.org/3/reference/expressions.html#in>) and [` not in `](<https://docs.python.org/3/reference/expressions.html#not-in>), are supported by types that are [iterable](<https://docs.python.org/3/glossary.html#term-iterable>) or implement the [` __contains__() `](<https://docs.python.org/3/reference/datamodel.html#object.__contains__>) method.

> Source: [` Built-in Types | Comparisons `](<https://docs.python.org/3/library/stdtypes.html#comparisons>)