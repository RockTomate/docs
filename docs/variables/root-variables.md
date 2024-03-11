---
id: root-variables
title: Root Variables
---

## Introduction

Root variables are RockTomate's built-in variables that can be used from anywhere. They can be constant or dynamic. Examples would be a project directory path or even the name of a currently running job.

To see all available root variables, click the “Root” tab in "Variable Manager" window. You'll be able to see values of constant root variables right away, but dynamic variables are marked as `<dynamic variable>`.

![](/assets/variables/root-variables.png)

Right-clicking a variable will let you copy it to the clipboard to save the trouble of typing it manually.

## References

| Variable                     | Type                      | Description                                                                                                                        |
| ---------------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `%AbsoluteURL%`              | `String`                  | The URL of the document. For WebGL, this a web URL. For Android, iOS, or Universal Windows Platform (UWP) this is a deep link URL. |
| `%AltDirSeparatorChar%`      | `Char`                    | The currently supported directory separator.                                                                                       |
| `%AppDataDir%`               | `String`                  | Path to the "AppData" directory of the local machine.                                                                              |
| `%AppVersion%`               | `String`                  | Current version of the player application.                                                                                         |
| `%AssetsDir%`                | `String`                  | File path to the "Assets" directory of the Unity project.                                                                          |
| `%LibraryDir%`               | `String`                  | File path to the "Library" directory of the Unity project.                                                                         |
| `%BuildGUID%`                | `String`                  | GUID of this player build (Unity 5.6 and above).                                                                                   |
| `%CloudProjectID%`           | `String`                  | Cloud Project GUID.                                                                                                                |
| `%CommandLineArgs%`          | `String[]`                | Command line arguments that were launched with this Unity executable.                                                              |
| `%CompanyName%`              | `String`                  | Name of the company as specified in Project Settings.                                                                              |
| `%CompileSymbols%`           | `String[]`                | Compile Symbols of the Target Platform.                                                                                            |
| `%CurrentBuildTarget%`       | `BuildTarget`             | Current build target selected for this project.                                                                                    |
| `%CurrentTime%`              | `DateTime`                | Local time.                                                                                                                        |
| `%DesktopDir%`               | `String`                  | Leads to a desktop directory of this user.                                                                                         |
| `%DirSeparatorChar%`         | `Char`                    | Character separator for directories.                                                                                               |
| `%HasProLicense%`            | `Boolean`                 | Whether or not this User has a Pro License.                                                                                        |
| `%InstallerName%`            | `String`                  | Name of the installer.                                                                                                             |
| `%InstallMode%`              | `ApplicationInstallMode`  | Install mode                                                                                                                       |
| `%IsBatchMode%`              | `Boolean`                 | Whether this Unity executable was launched in batch mode.                                                                          |
| `%IsBuilding%`               | `Boolean`                 | Whether this Unity Editor is building anything.                                                                                    |
| `%IsCompiling%`              | `Boolean`                 | Whether this Unity Editor is compiling anything.                                                                                   |
| `%IsConsole%`                | `Boolean`                 | Whether the current build target is console-related (e.g PS4).                                                                     |
| `%IsEditor%`                 | `Boolean`                 | Whether we're running inside Unity editor.                                                                                         |
| `%IsMobile%`                 | `Boolean`                 | Whether the current build target is mobile-related (e.g iOS).                                                                      |
| `%IsOnline%`                 | `Boolean`                 | Whether this machine has access to the Internet.                                                                                   |
| `%IsPaused%`                 | `Boolean`                 | Whether Play Mode has been paused.                                                                                                 |
| `%IsPlaying%`                | `Boolean`                 | Whether the Play Mode is playing.                                                                                                  |
| `%IsTempProject%`            | `Boolean`                 | Whether this is the temporary Unity project.                                                                                       |
| `%LocalAppDataDir%`          | `String`                  | Directory path of LocalAppData of this machine.                                                                                    |
| `%NewLine%`                  | `String`                  | New line.                                                                                                                          |
| `%PathSeparatorChar%`        | `Char`                    | Character separator for paths.                                                                                                     |
| `%PersistentDataDir%`        | `String`                  | Paths to a persistent data directory.                                                                                              |
| `%ProductName%`              | `String`                  | Product Name as specified in Project Settings.                                                                                     |
| `%ProjectDir%`               | `String`                  | Root directory of this project.                                                                                                    |
| `%RunningJobId%`             | `String`                  | GUID of a currently running Job.                                                                                                   |
| `%RunningJobName%`           | `String`                  | Name of a currently running Job.                                                                                                   |
| `%RunningJobPath%`           | `String`                  | File path of a currently running Job.                                                                                              |
| `%StreamingAssetsDir%`       | `String`                  | Path to Streaming Assets directory.                                                                                                |
| `%SystemLanguage%`           | `SystemLanguage`          | Current system language of this machine.                                                                                           |
| `%TargetPlatforms%`          | `BuildTarget[]`           | All valid platforms this Unity engine can build to.                                                                                |
| `%TempCacheDir%`             | `String`                  | Path to temporary/cache directory.                                                                                                 |
| `%TimeSinceStartup%`         | `Double`                  | Time passed (in seconds) since this Unity editor has started.                                                                      |
| `%UnityDir%`                 | `String`                  | Directory to the executable of this Unity engine                                                                                   |
| `%UnityVersion%`             | `String`                  | Version of this Unity Editor.                                                                                                      |
| `%VolumeSeparatorChar%`      | `Char`                    | Character separator for volumes.                                                                                                   |
| `%WorkDir%`                  | `String`                  | Current working directory.                                                                                                         |
| `%ScriptableRuntimeVersion%` | `ScriptingRuntimeVersion` | Unity project's scriptable runtime version.                                                                                        |
| `%IsGitRepo%`                | `Boolean`                 | Whether this project is a Git repository.                                                                                          |
| `%GitLastCommitHash%`        | `String`                  | Commit hash (SHA format) of the last commit. Empty if the current project is not a Git repository.                                 |
| `%GitCurrentBranch%`         | `String`                  | Name of a currently checked out branch. Empty if the current project is not a Git repository.                                      |
| `%IncludedScenesInBuild%`    | `String[]`                | Scene paths of all scenes that are included in build configuration.                                                                |
| `%AllScenesInBuild%`         | `String[]`                | Scene paths of all scenes that are included in build configuration (including disabled ones).                                      |
