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

## Running using Shortcuts

> Requires Unity 2019.1 or newer

You can also configure RockTomate to run specific jobs by pressing a combination of shortcut keys. You can map up to 10 jobs to 10 different shortcuts.

Before we can specify shortcuts, we need to map a job asset to one of 10 available slots.

You can do so by going to **Edit/Preferences/RockTomate** menu.

![](assets/workflows/shortcut-mapping-preferences-menu.png)

Once that done, you can navigate to **Edit/Shortcuts/RockTomate** and specify shortcut key for your mapping.

![](assets/workflows/unity-shortcut-settings-rocktomate-mapping.png)

And that's it! Triggering a shortcut will run a Job of your choosing. In the example above, pressing `CTRL + 1` will trigger a `BuildAllPlatforms` job.

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

> The asset file must be inside of Unity project and acknowledged by the AssetDatabase (call `AssetDatabase.Refresh()` for that).<br><br>
> Note that these functions won't wait for the Job to finish and will exit immediately after being called.

### Stopping Job

Call this function if you want to stop a currently running Job.

```csharp
HardCodeLab.RockTomate.Jobs.Stop();
```

## Running from CLI

Jobs can be executed from the command line interface while running Unity engine in batch mode.

You can read more about this method [here](advanced/running-from-cli.md).