---
id: creating-step
title: Creating Step
---

RockTomate has a flexible framework which allows you to create your own Steps and reuse them across different jobs with no hassle.

We’ll be making a step that takes two integers, executes a mathematical operation on them, and returns an outcome.

## Creating a Class

First things first, create a C# script inside of an Editor folder, or make sure it’s within an assembly definition which will be compiled only in Editor. 

To make things easier to manage, place the script inside of `RockTomate/Scripts/Steps/` directory. Let’s name our script `MathStep`.

Add the following namespaces:

```csharp
using HardCodeLab.RockTomate.Core.Steps;
using HardCodeLab.RockTomate.Core.Attributes;
```

Have our `MathStep` class derive from `SimpleStep` class. Implement a missing method and have it return `true` for now.

Above our `MathStep` class declaration, add the following attribute:

```csharp
[StepDescription("Math", "Does a math operation", "Mathematics")]
```

This tells RockTomate surface information about the step. In this case, it tells its name, gives description and associated category. Without this attribute, Step won't show up in the Step Browser window.

This is how `MathStep` class should look like:

```csharp
using HardCodeLab.RockTomate.Core.Steps;
using HardCodeLab.RockTomate.Core.Attributes;

[StepDescription("Math", "Does a math operation", "Mathematics")]
public class MathStep : SimpleStep
{
    protected override bool OnStepStart()
    {
        return true;
    }
}
```

Now, if you go back to Unity and let it compile our changes, we should see new Step in the Step Browser window.

![](/products/rocktomate/assets/advanced/new-step-in-step-browser-window.png)

## Test