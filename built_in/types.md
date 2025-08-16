# Built-in Types


## Table of Contents
- [Truth Value Testing](<#truth-value-testing>)
- [Boolean Operations](<#boolean-operations>)
- [Numeric Types](<#numeric-types>)
- [Bitwise Operations on Integer Types](<#bitwise-operations-on-integer-types>)


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


## Numeric Types

There are three distinct numeric types: *integers*, *floating-point numbers*, and *complex numbers*. In addition, Booleans are a subtype of integers. Integers have unlimited precision. Floating-point numbers are usually implemented using ` double ` in C. Complex numbers have a real and imaginary part, which are each a floating-point number. To extract these parts from a complex number ` z `, use ` z.real ` and ` z.imag `.

Numbers are created by numeric literals or as the result of built-in functions and operators. Unadorned integer literals yield integers. Numeric literals containing a decimal point or an exponent sign yield floating-point numbers. Appending ` 'j' ` or ` 'J' ` to anumeric literal yields an imaginary number which you can add to an integer or float to get a complex number with real and imaginary parts.

Python fully supports mxied arithmetic: when a binary arithmetic operator has operands of different numeric types, the operand with the "narrower" type is widened to that of the other, where integer is narrower than floating-point, which is narrower than xomples. A comparison between numbers of different types behaves as though the exact values of those numbers were being compared.

The constructors [` int() `](<https://docs.python.org/3/library/functions.html#int>), [` float() `](<https://docs.python.org/3/library/functions.html#float>), and [` complex() `](<https://docs.python.org/3/library/functions.html#complex>) can be used to produce numbers of a specific type.

All numeric types (except complex) support the following operations (for priorities of the operations, see [Operator precendence](<https://docs.python.org/3/reference/expressions.html#operator-summary>)):

| Operations          | Result                                                                                  | Notes  | Full documentation                                                          |
|---------------------|-----------------------------------------------------------------------------------------|--------|-----------------------------------------------------------------------------|
| ` x + y `           | sum of ` x ` and ` y `                                                                  |        |                                                                             |
| ` x - y `           | difference of ` x ` and ` y `                                                           |        |                                                                             |
| ` x * y `           | product of ` x ` and ` y `                                                              |        |                                                                             |
| ` x / y `           | quotient of ` x ` and ` y `                                                             |        |                                                                             |
| ` x // y `          | floored quotient of ` x ` and ` y `                                                     | (1)(2) |                                                                             |
| ` x % y `           | remained of ` x / y `                                                                   | (2)    |                                                                             |
| ` -x `              | ` x ` negated                                                                           |        |                                                                             |
| ` +x `              | ` x ` unchanged                                                                         |        |                                                                             |
| ` abs(x) `          | absolute value or magnitude of ` x `                                                    |        | [` abs() `](<https://docs.python.org/3/library/functions.html#abs>)         |
| ` int(x) `          | ` x ` converted to integer                                                              | (3)(6) | [` int() `](<https://docs.python.org/3/library/functions.html#int>)         |
| ` float(x) `        | ` x ` converted to floating point                                                       | (4)(6) | [` float() `](<https://docs.python.org/3/library/functions.html#float>)     |
| ` complex(re, im) ` | a complex number with real part ` re `, imaginary part ` im `. ` im ` defaults to zero. | (6)    | [` complex() `](<https://docs.python.org/3/library/functions.html#complex>) |
| ` c.conjugate() `   | conjugate of the complex number ` c `                                                   |        |                                                                             |
| ` divmod(x, y) `    | the pair ` (x // y, x % y) `                                                            | (2)    | [` divmod() `](<https://docs.python.org/3/library/functions.html#divmod>)   |
| ` pow(x, y) `       | ` x ` to the power ` y `                                                                | (5)    | [` pow() `](<https://docs.python.org/3/library/functions.html#pow>)         |
| ` x ** y `          | ` x ` to the power ` y `                                                                | (5)    |                                                                             |


Notes:

1. Also referred to as integer division. For operands of type [` int `](<https://docs.python.org/3/library/functions.html#int>), the result has type [` int `](<https://docs.python.org/3/library/functions.html#int>). For operands of type [` float `](<https://docs.python.org/3/library/functions.html#float>), the result has type [` float `](<https://docs.python.org/3/library/functions.html#float>). In general, the result is a whole integer, though the result's type is not necessarily [` int `](<https://docs.python.org/3/library/functions.html#int>). The result is always rounded towards minus infinity: ` 1 // 2 ` is ` 0 `, ` (-1) // 2 ` is ` -1 `, ` 1 // (-2) ` is ` -1 `, and ` (-1) // (-2) ` is ` 0 `.

2. Not for complex numbers. Instead convert to floats using [` abs() `](<https://docs.python.org/3/library/functions.html#abs>) if appropriate.

3. Conversion from [` float `](<https://docs.python.org/3/library/functions.html#float>) to [` int `](<https://docs.python.org/3/library/functions.html#int>) truncates, discarding the fractional part.

4. Float also accepts the strings "nan" and "inf" with an optional prefix "+" or "-" for Not a Number (NaN) and positive or negative infinity.

5. Python defines ` pow(0, 0) ` and ` 0 ** 0 ` to be ` 1 `, as is common for programming languages.

6. The numeric literals accepted include the digits ` 0 ` to ` 9 ` or any Unicode equivalent (code points with the ` Nd ` property).


All [` numbers.Real `](<https://docs.python.org/3/library/numbers.html#numbers.Real>) types ([` int `](<https://docs.python.org/3/library/functions.html#int>) and [` float `](<https://docs.python.org/3/library/functions.html#float>)) also include the following operations:

| Operation                                                                     | Result                                                                                                 |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| [` math.trunc(x) `](<https://docs.python.org/3/library/math.html#math.trunc>) | ` x ` truncated to [` Integral `](<https://docs.python.org/3/library/numbers.html#numbers.Integral>)   |
| [` round(x[, n]) `](<https://docs.python.org/3/library/functions.html#round>) | ` x ` rounded to ` n ` digits, rounding half to even. If ` n ` is omitted, it defaults to 0.           |
| [` math.floor(x) `](<https://docs.python.org/3/library/math.html#math.floor>) | the greated [` Integral `](<https://docs.python.org/3/library/numbers.html#numbers.Integral>) <= ` x ` |
| [` math.ceil(x) `](<https://docs.python.org/3/library/math.html#math.ceil>)   | the least [` Integral `](<https://docs.python.org/3/library/numbers.html#numbers.Integral>) >= ` x `   |



### Bitwise Operations on Integer Types


Bitwise operations only make sense for integers. The result of bitwise operations is calculated as though carried out in two's complement with an infinite number of sign bits.

The priorities of the binary bitwise operations are all lower than the numeric operations and higher than the comparisons; the unary operation ` ~ ` has the same priority as the other unary numeric operations.

This table lists the bitwise operations sorted in ascending priority:


| Operation  | Result                               | Notes  |
|------------|--------------------------------------|--------|
| ` x | y `  | bitwise OR of ` x ` and ` y `        | (4)    |
| ` x ^ y `  | bitwise EXCLUSIVE of ` x ` and ` y ` | (4)    |
| ` x & y `  | bitwise AND of ` x ` and ` y `       | (4)    |
| ` x << n ` | ` x ` shifted left by ` n ` bits     | (1)(2) |
| ` x >> n ` | ` x ` shifted right by ` n ` bits    | (1)(3) |
| ` ~x `     | the bits of ` x ` inverted           |        |


Notes:

1. Negative shift counts are illegal and cause a [` ValueError `](<https://docs.python.org/3/library/exceptions.html#ValueError>) to be raised.

2. A left shift by ` n ` bits is equivalent to multiplication by ` pow(2, n) `.

3. A right shift by ` n ` bits is equivalent to floor division by ` pow(2, n) `.

4. Performing these calculations with at least one extra sign extension bit in a finit two's complement representation is sufficient to get the same result as if there were an infinite number of sign bits.