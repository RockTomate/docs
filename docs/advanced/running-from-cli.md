---
id: running-from-cli
title: Running from CLI
---

You can also run RockTomate jobs from the command-line interface when you’re running Unity in batch mode. 

To do so, you must pass the following argument to Unity.exe

```shell
-executeMethod "HardCodeLab.RockTomate.Jobs.Run" "Assets/AutomatedJob.rock.job"
```

> Do not pass `-quit` argument when running a Job as it would immediately close Unity without letting Job to finish. This is because RockTomate was designed to be a non-blocking process to let users interact with UI while the Job is running.<br><br>
RockTomate automatically quits Unity engine after it's done executing the Job (regardless of whether it passed or failed).

## Passing Variables

Aside from running jobs, you can also map variables with values from command line arguments.

For example, let’s say we have a variable named `my_pet` and want to pass a value `Shiba Inu`. We can do the following:

```shell
-executeMethod "HardCodeLab.RockTomate.Jobs.Run" "Assets/AutomatedJob.rock.job" "my_pet"="Shiba Inu"
```

You can map as many variables as you’d like.

## Mapping Variables

Alternatively, variables can be mapped directly in advance.

When creating a variable, set its value to be a formula `%arg0%`.

![](assets/advanced/creating-mappable-variable.png)

Then, you can run a Job without explicitly stating variable names.

```shell
-executeMethod "HardCodeLab.RockTomate.Jobs.Run" "Assets/AutomatedJob.rock.job" "Shiba Inu"
```