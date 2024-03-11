---
id: variable-banks
title: Variable Banks
---

Variable Banks are a set of variables that can be re-used across multiple jobs. Unlike custom variables, they're stored in a separate .asset file and can be referenced by the Job. Variable banks are ideal for situations when multiple jobs need to share same custom variables.

A single Job can reference multiple variable banks.

Just like anything else, variable bank references can either be directly referenced or resolved by a formula.

![](/assets/variables/variable-banks.png)

## Creating a Variable Bank

To create a Variable Bank, in the Assets window, navigate to `Create > RockTomate > Variable Bank`. This should now create a variable bank asset.

Double click on a variable bank and a familiar window pops up.

![](/assets/variables/variable-bank-editor.png)

From there, the workflow is the same as if you were creating custom variables for a Job: click + icon and create your desired variable. Once done, close the window.

## Adding a reference

To add a variable bank reference, navigate to “External” tab and click + icon. A field will pop up prompting you to add a variable bank reference. You can then directly add it by dragging it or resolve it through formula mode.

Alternatively, you can also drag one or more variable bank assets into “External” area to add them as references.

Now, just like an ordinary variable, you can refer to them in your formulas!
