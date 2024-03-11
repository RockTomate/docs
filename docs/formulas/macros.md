---
id: macros
title: Using Macros
---

Macros are lightweight functions that accept parameters and return a value: just like an ordinary function. They're called from within formulas.

To learn about available macros, see [Macro References](/references/macro-references).

## Calling Macros

Inside of a formula, macros can be called just like an ordinary function:

```
macro1(arg1)
```

## Passing Variables

Naturally, you can pass variables into macros:

```
macro1(%VAR_NAME%)
```

## Passing Macros

Macros can also be nested within each other

```
macro1(arg1, macro2(arg2, arg3))
```

## Passing Whitespace

By default, whitespace characters are trimmed off parameters, but this can be prevented by surrounding your arguments in quotation marks `"`.

```
length(Hello )

Output: 5
```

And if we use quotation marks:

```
length("Hello ")

Output: 6
```

This works with any type of arguments that you supply including variables and macros.

```
sum("%VAR_TEN%", "sum("10", "10")")

Output: 30
```

## Escaping Quotation Marks

Quotation marks can be escaped using an additional set of quotation marks.

```
length("")
Output: 0

length("""")
Output: 2
```
