# Built-in Types


## Table of Contents
- [Truth Value Testing](<#truth-value-testing>)


## Truth Value Testing

Any object that can be tested for truth value, for use in an [` if `](<https://docs.python.org/3/reference/compound_stmts.html#if>) or [` while `](<https://docs.python.org/3/reference/compound_stmts.html#while>) statement condition or as operated of the Boolean operations below.

By default, an object is considered true unless its class defines either a [` __bool__() `](<https://docs.python.org/3/reference/datamodel.html#object.__bool__>) method that returns ` False ` or a [` __len__() `](<https://docs.python.org/3/reference/datamodel.html#object.__len__>) method that returns zero, when called with the object. Here are most of the built-in objects considered false:
- constants defined to be false: ` None ` and ` False `
- zero of any numeric type: ` 0 `, ` 0.0 `, ` 0j `, ` Decimal(0) `, ` Fraction(0, 1) `
- empty sequences and collections: ` '' `, ` () `, ` [] `, ` {} `, ` set() `, ` range(0) `

> Source: [` Built-in Types | Truth Value Testing `](<https://docs.python.org/3/library/stdtypes.html#truth-value-testing>)