---
id: output-fields
title: Output Fields
---

Some steps, like "Resolve Paths" do nothing but return a value. Those values can be accessed using output fields.

Output fields ask for the name of a variable to pass resultant value to.

## Example Usage

We want to append multiple strings into one. To do that, we'll use "Append to String" Step.

1. Populate input fields.

![](assets/formulas/append-to-string-input-fields.png)

2. Go to "Output Fields" tab, and give it variable name to save to.

![](assets/formulas/append-to-string-output-fields.png)

3. Add "Print Log" Step and have it print out `%result%` variable.

4. Run the Job and observe the console window

![](assets/formulas/printed-append-to-string-result.png)

## Variable Scope

As you may have noticed, we didn't need to define a variable at design-time, it's been created at runtime. 

Be aware that dynamically created variables are available only in the current scope. Meaning, if you've created this variable within another Step such as "Loop" or "Group", it won't be available outside. 

Logically, it will be available anywhere if the variable has been dynamically created at the root.

If output field is supplied with an already existing variable then it will be modified like usual.

## Updating Variables

If you supply a variable name, the value will be updated. However, sometimes you may want to add a new value to an existing variable. For example, we may want to add a new value to a collection variable.

To do that, we use special output field macro `add_to`.

```
add_to(%VAR_LIST_TO_ADD_TO%)
```

So if there's a variable of array `["Hello", "World"]` and output field has `"!!!"`, then the variable will be updated to `["Hello", "World", "!!!"]` instead of `["!!!"]`.