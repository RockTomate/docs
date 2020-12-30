---
id: running-from-cli
title: Running from CLI
---

You can also run RockTomate jobs from the command-line interface when you’re running Unity in batch mode. 

```shell
"D:\Unity\2017.4.27f1\Editor\Unity.exe" -batchMode -projectPath "D:\Projects\HardCodeLab\RockTomate" -executeMethod "HardCodeLab.RockTomate.CLI.RunJob" "Assets/AutomatedJob.rock.job"
```

## Arguments

| Argument       | Parameter(s)                                                      | Description                                            |
|----------------|-------------------------------------------------------------------|--------------------------------------------------------|
| -batchMode     | *none*                                                            | Makes Unity run in batch mode                          |
| -projectPath   | "D:\Projects\HardCodeLab\RockTomate"                              | Opens a Unity project                                  |
| -executeMethod | "HardCodeLab.RockTomate.CLI.RunJob"  "Assets/AutomatedJob.rock.job" | Runs a Job with path of "Assets/AutomatedJob.rock.job" |

You can find the full list of Unity's command line arguments [here](https://docs.unity3d.com/Manual/CommandLineArguments.html).

> Do not pass `-quit` argument when running a Job as it would immediately closes Unity without letting the Job to finish. This is because RockTomate was designed to be a non-blocking process to let users interact with UI while the Job is running.<br><br>
RockTomate will quit Unity after the Job has done running (passing `0` as the exit code if it succeeded or `1` if it failed).

## Passing Variables

Aside from running jobs, you can also map variables with values from command line arguments.

For example, let’s say we have a variable named `my_pet` and want to pass a value `Shiba Inu`. We can do the following:

```shell
-executeMethod "HardCodeLab.RockTomate.CLI.RunJob" "Assets/AutomatedJob.rock.job" "my_pet"="Shiba Inu"
```

You can map as many variables as you’d like.

## Mapping Variables

Alternatively, variables can be mapped directly in advance.

When creating a variable, set its value to be a formula `%arg0%`.

![](assets/advanced/creating-mappable-variable.png)

Then, you can run a Job without explicitly stating variable names.

```shell
-executeMethod "HardCodeLab.RockTomate.CLI.RunJob" "Assets/AutomatedJob.rock.job" "Shiba Inu"
```