---
id: variable-overriding
title: Variable Overriding
---

There is no restriction on having multiple variables with same names. It's possible to create a custom variable name with the same name as a root variable, but in doing so it will override the root variable.

It's important to be aware of the order in which variables are searched when requested through the formulas.

This is the order in which variables are searched for:

1. Temporary variables in-scope (e.g loop variable)
2. Job variables
3. Variable banks (in order added)
4. Root variables