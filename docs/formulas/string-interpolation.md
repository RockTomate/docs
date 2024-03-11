---
id: string-interpolation
title: String Interpolation
---

While it's possible to run macros in a formula, it was impossible to combine string and macro results together without putting macro results into a variable first.

For example:

```
2 plus 2 equals sum(2,2)
```

Would not evaluate and throw an error instead.

A quick workaround to this would be to place the result of `sum(2, 2)` into a separate variable and reference that variable instead.

Such excess work can now be avoided by surrounding macros with curly braces `{}`:

```
2 plus 2 equals {sum(2,2)}
```

This will safely evaluate to:

```
2 plus 2 equals 4
```
