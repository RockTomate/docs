---
id: root-variables
title: Root Variables
---

Root variables are RockTomate's built-in variables that can be used from anywhere. They can be constant or dynamic. Examples would be a project directory path or even the name of a currently running job.

To see all available root variables, click the “Root” tab in "Variable Manager" window. You'll be able to see values of constant root variables right away, but dynamic variables are marked as `<dynamic variable>`.

![](/assets/variables/root-variables.png)

Right-clicking a variable will let you copy it to the clipboard to save the trouble of typing it manually.

## References

| Variable | Type | Description |
|----------|------|-------------|
| `%AbsoluteURL%` | `String` | The URL of the document. For WebGL, this a web URL. For Android, iOS, or Universal Windows Platform (UWP) this is a deep link URL.
| `%AltDirSeparatorChar%` | `Char` | The currently supported directory separator. |
| `%AppDataDir%` | `String` | Path to the "AppData" directory of the local machine. |
| `%AppVersion%` | `String` | Current version of the player application. |
| `%AssetsDir%` | `String` | File path to the "Assets" directory of the Unity project. |
| `%BuildGUID%` | `String` | GUID of this player build |
| `%CloudProjectID%` | `String` | |
| `%CommandLineArgs%` | `String[]` | |
| `%CompanyName%` | `String` | |
| `%CompileSymbols%` | `String[]` | |
| `%CurrentBuildTarget%` | `BuildTarget` | |
| `%CurrentTime%` | `DateTime` | |
| `%DesktopDir%` | `String` | |
| `%DirSeparatorChar%` | `Char` | |
| `%HasProLicense%` | `Boolean` | |
| `%InstallerName%` | `String` | |
| `%InstallMode%` | `ApplicationInstallMode` | |
| `%IsBatchMode%` | `Boolean` | |
| `%IsBuilding%` | `Boolean` | |
| `%IsCompiling%` | `Boolean` | |
| `%IsConsole%` | `Boolean` | |
| `%IsEditor%` | `Boolean` | |
| `%IsMobile%` | `Boolean` | |
| `%IsOnline%` | `Boolean` | |
| `%IsPaused%` | `Boolean` | |
| `%IsPlaying%` | `Boolean` | |
| `%IsTempProject%` | `Boolean` | |
| `%LocalAppDataDir%` | `String` | |
| `%NewLine%` | `String` | |
| `%PathSeparatorChar%` | `Char` | |
| `%PersistentDataDir%` | `String` | |
| `%ProductName%` | `String` | |
| `%ProjectDir%` | String`` | |
| `%RunningJobId%` | `String` | |
| `%RunningJobName%` | `String` | |
| `%RunningJobPath%` | `String` | |
| `%StreamingAssetsDir%` | `String` | |
| `%SystemLanguage%` | `SystemLanguage` | |
| `%TargetPlatforms%` | `Boolean` | |
| `%TempCacheDir%` | `String` | |
| `%TimeSinceStartup%` | `Double` | |
| `%UnityDir%` | `String` | |
| `%UnityVersion%` | `String` | |
| `%VolumeSeparatorChar%` | `Char` | |
| `%WorkDir%` | `String` | |