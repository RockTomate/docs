---
id: running-job
title: Running Job
---

There are multiple ways of running a Job.

## Running from GUI

The standard way is by pressing the Play button in [Job Editor Window](ui/job-editor-window.md).

![](assets/workflows/running-job-from-gui.gif)

## Running from Context Menu

In the Project Window, locate the job that you'd like to run, right-click it and select `RockTomate > Run Job`

![](assets/workflows/running-job-from-context-menu.gif)

## Running from C# Script

You can run a job by calling a C# script

### Starting Job

```csharp
HardCodeLab.RockTomate.Jobs.Start("Assets/AutomatedJob.rock.job.asset");
```

Alternatively, you can pass the variable of type `Job` into function.

```csharp
HardCodeLab.RockTomate.Jobs.Start(jobAssetFileReference);
```

> The asset file must be inside of Unity project and acknowledged by the AssetDatabase (call AssetDatabase
> Note that these functions won't wait for the Job to finish and will immediately exit after being called.

### Stopping Job

Call this function if you want to stop a currently running Job.

```csharp
HardCodeLab.RockTomate.Jobs.Stop();
```

## Running from CLI

Jobs can be executed from the command line interface while running Unity engine in batch mode.

You can read more about this method [here](advanced/running-from-cli.md).