---
id: creating-macro
title: Creating a Macro
---

In this guide, we'll create a macro that concatenates 2 strings into one.

By the end of this tutorial, we intend to call the following macro inside of a formula field.

```
concat(Hello_, World!)
```

And get this as a result:

```
Hello_World!
```

## Creating a Class

Create an empty C# class (name it `ConcatMacro`) and place it inside of `Assets/RockTomate/Scripts/Macros/Input` directory.

> The naming conversion is to always end your macro classes with "Macro".

Add the following namespaces:

```csharp
using HardCodeLab.RockTomate.Core.Data;
using HardCodeLab.RockTomate.Core.Enums;
using HardCodeLab.RockTomate.Core.Attributes;
```

Have our `ConcatMacro` class derive from `BaseMacro<string>` class (where `string` is the return type).

Above our `ConcatMacro` class declaration, add the following attribute:

```csharp
[Macro(FieldType.Input, "concat")]
```

The attribute above helps RockTomate identify what kind of macro `ConcatMacro` is and how should it be identified in formula fields.

## Specifying Parameters

Macro classes require us to explicitly state what parameters it expects, their type and their short description. To do that, we implement the following method with following types:

```csharp
protected override MacroParameter[] GetParameters()
{
    return new[]
    {
        MacroParameter.Create<string>("First string."),
        MacroParameter.Create<string>("Second string."),
    };
}
```

> There's no need to cache a return value as `BaseMacro` handles that by itself.

## Implementing a Macro

Finally, we can start implementing macro logic.

Add the following:

```csharp
protected override string OnInvoke(JobContext context, params object[] args)
{
    return "";
}
```

Let's go through the arguments.

### `context`

Stores the current job context, which mainly consists of currently defined variables and their values. You don't need that unless you're making a macro for an output field where updating a variable is more important.

### `args`

This is where all passed arguments go. However, they cannot be used right off the bat as they're not casted to an appropriate type. We'll look into doing that shortly.

## Retrieving Arguments

We need to cast arguments to an appropriate type. A reasonable solution to this is doing just that:

```csharp
var firstString = (string)args[0];
var secondString = (string)args[1];
```

However, `BaseMacro` has a helper function that not only does that, but also handles errors.

```csharp
var firstString = GetArg<string>(args, 0);
var secondString = GetArg<string>(args, 1);
```

## Implementing Logic

Finally, we can implement actual macro logic.

It's pretty straight-forward so let's do that:

```csharp
protected override string OnInvoke(JobContext context, params object[] args)
{
    var firstString = GetArg<string>(args, 0);
    var secondString = GetArg<string>(args, 1);

    return firstString + secondString;
}
```

And we're done! After compilation, the macro will be registered automatically and can be called just like any other macro.

Full C# Script:

```csharp
using HardCodeLab.RockTomate.Core.Data;
using HardCodeLab.RockTomate.Core.Enums;
using HardCodeLab.RockTomate.Core.Attributes;

[Macro(FieldType.Input, "concat")]
public class ConcatMacro : BaseMacro<string>
{
    protected override MacroParameter[] GetParameters()
    {
        return new[]
        {
            MacroParameter.Create<string>("First string."),
            MacroParameter.Create<string>("Second string."),
        };
    }

    protected override string OnInvoke(JobContext context, params object[] args)
    {
        var firstString = GetArg<string>(args, 0);
        var secondString = GetArg<string>(args, 1);

        return firstString + secondString;
    }
}
```
