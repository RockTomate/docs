---
id: macros
title: Macros
---

Macros are lightweight functions that accept parameters and return a value: just like an ordinary function. They're called from within formulas.

## Using Macros

Inside of a formula, macros can be called just like an ordinary function:

```
macro1(arg1)
```

## Passing Variables

Naturally, you can pass variables into macros:

```
macro1(%VAR_NAME%)
```

## Passing other Macros

Macros can also be nested within each other

```
macro1(arg1, macro2(arg2, arg3))
```