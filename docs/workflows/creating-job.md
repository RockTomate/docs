---
id: creating-job
title: Creating Job
---

Here we'll go through the workflow of creating a simple Job, add and setup Steps and run everything.

For this tutorial, we'll create a Job that prints all scene paths inside of `Assets` folder.

## Creating a Job file

1. In project window, right-click and go to `Create > RockTomate > Job`.

![](assets/workflows/create-job-context-menu.png)

An asset file will be created with an extension of `rock.job.asset` (in Unity it will show up as `rock.job`). While the extension doesn't do much, it's recommended to keep it to make searching easier.

2. Double-click a newly created job and it will open in [Job Editor Window](ui/job-editor-window.md). The window will open if it's closed or will be focused on if hidden in a different tab.

![](assets/workflows/empty-job-editor-window.png)

## Adding steps

For what we're trying to achieve, we would need the following steps:

-   Loop - iterating through any collection item (List, Array etc.)
-   Print Log - prints any object in a Unity console.

1. In [Step Browser Window](ui/step-browser-window.md), locate and double-click on `Loop` step to add it to the job.
2. Locate Print Log and drag it on top of the loop. Loop step is a special step which accepts child steps.

If everything is done right, this is how your Job should look like.

![](assets/workflows/added-loop-print-steps.png)

## Editing Properties

To access steps' properties, simply click on it in the Job Editor Window. Your Inspector Window (unless it's closed) will show Step properties.

### Loop Step

#### Item List

This field only accepts formulas. Formulas should return a value which could be equivalent to a collection. If resultant value is not an array, it will be converted to one. (see [Type Conversion](advanced/type-conversion.md) section to know more)

We'll use `path` macro which requires two arguments: a path containing a wildcard and whether or not to convert paths to be relative to the `Assets` directory.

-   [Argument 1] We want to iterate through the whole `Assets` directory, so we'll use a root variable `%AssetsDir%` to get it. Then we add `/*.unity` to indicate that we want all file paths with `.unity` extension in that directory.
-   [Argument 2] We'll want to convert it so we'll set it to `true`.

This is our final formula: `path(%AssetsDir%/*.unity, true)`

#### Iterator Name

The name of the temporal variable that will be created inside of the `Loop` step. This variable represents an array item. Let's set it to `path`. Note that this variable will not be available outside of `Loop` step.

### Print Log Step

#### Message

Enable formula mode for this field, and put our local variable that we renamed earlier: `%path%`.

## Running Job

We're done! Now press the play button at the top and your Unity Console Window should be filled up with scene paths.

![](assets/workflows/printed-file-paths.png)

This Job could easily be re-purposed for doing more than printing Unity scenes. For example, we could open each Unity scene, bake lightmaps, then open another scene and repeat.

More importantly, this will scale as you add more scenes into the project as the macro will get **all** unity scenes.
