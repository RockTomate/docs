---
id: step-references
title: Step References
---

Here, you'll find information about steps, what they do, their properties and examples. 

You can jump to any step through the sidebar.

## Asset Store Publisher

### Upload to Asset Store

Compresses files into a .unitypackage and uploads it to the Asset Store Dashboard. This utility tool is useful for uploading asset updates to the Asset Store.

#### Input Fields

| Field                  | Required | Description                                                                                                                  |
| ---------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Package Id             | Yes      | This is the ID of the asset package for which assets will be uploaded to.                                                    |
| Username               | Yes      | Username of the Asset Store publisher account.                                                                               |
| Password               | Yes      | Password of the Asset Store publisher account.                                                                               |
| Asset Directory Path   | Yes      | Directory path which will be uploaded to the asset store. The path must be relative to the project's Assets directory.       |
| Include Dependencies   | No       | If true, then in addition to the assets paths listed, all dependent assets will be included as well.                         |
| Include Library Assets | No       | The exported package will include all library assets, ie. the project settings located in the Library folder of the project. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

## Assets

### Copy Asset

Creates a duplicate copy of an asset file.

#### Input Fields

| Field          | Required | Description                             |
| -------------- | -------- | --------------------------------------- |
| Asset Path     | Yes      | Path to a file that will be duplicated. |
| New Asset Path | Yes      | Path of a duplicated asset.             |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Create ScriptableObject

Creates an instance of ScriptableObject and saves it as an asset file.

#### Input Fields

| Field      | Required | Description                                                                                                                    |
| ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Class Name | Yes      | The type of the ScriptableObject to create, as the name of the type. For example, passing "Job" would create a RockTomate Job. |
| Asset Path | Yes      | Path where to save the created scriptable object.                                                                              |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Delete Asset

Deletes an asset file.

#### Input Fields

| Field      | Required | Description                                 |
| ---------- | -------- | ------------------------------------------- |
| Asset Path | Yes      | Path of an asset file that will be deleted. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Export UnityPackage

Exports asset files as a .unitypackage file.

#### Input Fields

| Field                  | Required | Description                                                                                                                                |
| ---------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| File Path              | Yes      | File path where .unitypackage file will be saved to. Must be relative to the project directory.                                            |
| Export Recursively     | No       | If true, will recurse through any subdirectories listed and include all assets inside them.                                                |
| Include Dependencies   | No       | If true, then in addition to the assets paths listed, all dependent assets will be included as well.                                       |
| Include Library Assets | No       | If true, then the exported package will include all library assets, ie. the project settings located in the Library folder of the project. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Refresh Asset Database

Refreshes an Asset Database of the project. Synchronously imports any changed assets into the project if any.

#### Input Fields

| Field                      | Required | Description                                                          |
| -------------------------- | -------- | -------------------------------------------------------------------- |
| Force Update               | No       | User initiate asset import                                           |
| Import Recursive           | No       | When a folder is imported, import all its contents as well.          |
| Download from Cache Server | No       | Force a full reimport and download the assets from the cache server. |
| Force Uncompressed Import  | No       | Forces asset import as uncompressed for edition facilities.          |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Set Labels

Sets labels for assets, replacing old ones in the process.

#### Input Fields

| Field       | Required | Description                                  |
| ----------- | -------- | -------------------------------------------- |
| Asset Paths | Yes      | Path to assets which labels will be updated. |
| Labels      | Yes      | New labels that will be set.                 |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

## Baking

### Bake Lightmap

Bakes a lightmap for a currently open scene

#### Input Fields

| Field       | Required | Description                                                  |
| ----------- | -------- | ------------------------------------------------------------ |
| Clear First | Yes      | If true, clear the initial lightmap before baking a new one. |

#### Output Fields

| Field                    | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| Is Success               | Returns true if this step has been executed successfully. |
| Lighting Data Asset Path | File path to a generated lighting data asset.             |

---

### Clear Lightmap

Clears lightmap data

#### Input Fields

| Field                     | Required | Description                                                                            |
| ------------------------- | -------- | -------------------------------------------------------------------------------------- |
| Clear Disk Cache          | Yes      | If true, clears the cache used by lightmaps, reflection probes and default reflection. |
| Clear Lighting Data Asset | Yes      | Remove the lighting data asset used by the current scene.                              |

#### Output Fields

| Field                    | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| Is Success               | Returns true if this step has been executed successfully. |

---

### Compute Occlusion Culling

Computes static Occlusion Culling of a currently active Scene.

#### Input Fields

| Field              | Required | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Smallest Occluder  | Yes      | The size of the smallest object that will be used to hide other objects when doing occlusion culling.Any objects smaller than this size will never cause objects occluded by them to be culled. For example, with a value of 5, all objects that are higher or wider than 5 meters will cause hidden objects behind them to be culled (not rendered, saving render time). Picking a good value for this property is a balance between occlusion accuracy and storage size for the occlusion data.                                                                                                                                                                                                     |
| Smallest Hole      | Yes      | This value represents the smallest gap between geometry through which the camera is supposed to see. The value represents the diameter of an object that could fit through the hole. If your scene has very small cracks through which the camera should be able to see, the Smallest Hole value must be smaller than the narrowest dimension of the gap.                                                                                                                                                                                                                                                                                                                                             |
| Backface Threshold | Yes      | Unity’s occlusion uses a data size optimization which reduces unnecessary details by testing backfaces. The default value of 100 is robust and never removes backfaces from the dataset. A value of 5 would aggressively reduce the data based on locations with visible backfaces. The idea is that typically, valid camera positions would not normally see many backfaces - for example, the view of the underside of a terrain , or the view from within a solid object that you should not be able to reach. With a threshold lower than 100, Unity will remove these areas from the dataset entirely, thereby reducing the data size for the occlusion. The value is clamped between 5 and 100. |

#### Output Fields

| Field                    | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| Is Success               | Returns true if this step has been executed successfully. |

---


## Building

### Build Asset Bundle

Builds all asset bundles specified in the editor.

#### Input Fields

| Field                                  | Required | Description                                                                                                                                                                                                                       |
| -------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Output Path                            | Yes      | Output path for the AssetBundles.                                                                                                                                                                                                 |
| Build Target                           | Yes      | Chosen target build platform.                                                                                                                                                                                                     |
| Compression                            | Yes      | Compression type that will be used when building asset bundles.<br>**Uncompressed** - Don't compress the data when creating the asset bundle.<br>**Chunk Based** - Use chunk-based LZ4 compression when creating the AssetBundle. |
| Append Hash                            | Yes      | Append the hash to the assetBundle name.                                                                                                                                                                                          |
| Force Rebuild                          | Yes      | Force rebuild the assetBundles.                                                                                                                                                                                                   |
| Deterministic                          | Yes      | Builds an asset bundle using a hash for the id of the object stored in the asset bundle.                                                                                                                                          |
| Dry Run Build                          | Yes      | Do a dry run build.                                                                                                                                                                                                               |
| Strict Mode                            | Yes      | Do not allow the build to succeed if any errors are reporting during it.                                                                                                                                                          |
| Load Asset By File Name                | Yes      | Enable Asset Bundle LoadAsset by file name.                                                                                                                                                                                       |
| Load Asset By File Name With Extension | Yes      | Enable Asset Bundle LoadAsset by file name with extension.                                                                                                                                                                        |
| Enable Write Type Tree                 | Yes      | Whether or not to include type information within the AssetBundle.                                                                                                                                                                |
| Ignore Type Tree Changes               | Yes      | Ignore the type tree changes when doing the incremental build check.                                                                                                                                                              |

#### Output Fields

| Field       | Description                                                                                                                                                                                                         |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Is Success  | Returns true if this step has been executed successfully.                                                                                                                                                           |

---

### Build Player

Builds a Project to an executable.

#### Input Fields

| Field                            | Required | Description                                                                                                                                                         |
| -------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Output Path                      | Yes      | The path where the application will be built. If given without extension, then this will act as a folder directory and will rely on a "File Name" field instead.    |
| File Name                        | No       | Name of the output file. This option will be used depending your "Build Target". Do not include file extension.                                                     |
| Scene Paths                      | No       | The scenes to be included in the build. If empty, the currently open scene will be built. Paths are relative to the project folder (Assets/MyLevels/MyScene.unity). |
| Asset Bundle Manifest Path       | No       | The path to an manifest file describing all of the asset bundles used in the build.                                                                                 |
| Build Target                     | Yes      | The platform to build.                                                                                                                                              |
| Development Build                | Yes      | *no description provided*                                                                                                                                           |
| Build Scripts Only               | Yes      | *no description provided*                                                                                                                                           |
| Build Additional Streamed Scenes | Yes      | *no description provided*                                                                                                                                           |
| Don't Compress Asset Bundle      | Yes      | *no description provided*                                                                                                                                           |

#### Output Fields

| Field                | Description                                               |
| -------------------- | --------------------------------------------------------- |
| Is Success           | Returns true if this step has been executed successfully. |
| Build Result         | Result of the build.                                      |
| Build Start          | Time when build has started.                              |
| Build End            | Time when build has ended.                                |
| Build Guid Id        | The GUId of the build.                                    |
| Build Error Count    | Number of errors occurred during the build.               |
| Build Warnings Count | Number of warnings occurred during the build.             |
| Build Size           | Total size of the build.                                  |
| Build Time           | Time taken (in milliseconds) for the build to complete.   |

---

### Compile DLL

Compiles C# scripts into DLL

#### Input Fields

| Field                        | Required | Description                                                                                                                                                                                                  |
| ---------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Output Path                  | Yes      | File path to where new DLL will be exported to.                                                                                                                                                              |
| Treat Warnings As Errors     | Yes      | If true, any warnings will cause compilation error.                                                                                                                                                          |
| Script Paths                 | Yes      | Scripts that will be compiled into a DLL.                                                                                                                                                                    |
| Resources                    | No       | Paths to resources that will be embedded into DLL.                                                                                                                                                           |
| Generate                     | Yes      | Specify whether or not we want to generate assembly info for this DLL. **Keep this option disabled if you plan to include an existing assembly info file, otherwise you'll end up with compilation errors!** |
| Assembly Version             | No       | Specify the version the DLL.<br>`[assembly: AssemblyVersion("..")]`                                                                                                                                          |
| File Version                 | No       | Value specifying the Win32 file version number. This normally defaults to the assembly version.<br>`[assembly: AssemblyFileVersion("..")]`                                                                   |
| Description                  | No       | A short description that summarizes the nature and purpose of the assembly.<br>`[assembly: AssemblyDescription("")]`                                                                                         |
| Company                      | No       | Value specifying a company name.<br>`[assembly: AssemblyCompany("")]`                                                                                                                                        |
| Copyright                    | No       | Value specifying copyright information.<br>`[assembly: AssemblyCopyright("")]`                                                                                                                               |
| Trademark                    | No       | Value specifying trademark information.<br>`[assembly: AssemblyTrademark("")]`                                                                                                                               |
| Product                      | No       | Value specifying product information.<br>`[assembly: AssemblyProduct("")]`                                                                                                                                   |
| Additional References        | No       | Paths to references.                                                                                                                                                                                         |
| Additional Compile Symbols   | No       | *no description provided*                                                                                                                                                                                    |
| Build Target Compile Symbols | No       | Specify from which build target should compile symbols be copied.                                                                                                                                            |
| Include Debug Info           | Yes      | Whether or not debug information should be included in the DLL.                                                                                                                                              |
| Optimize                     | Yes      | Whether DLL should be optimized.                                                                                                                                                                             |
| Unsafe                       | Yes      | Whether unsafe code should be allowed.                                                                                                                                                                       |
| Additional Arguments         | Yes      | Additional compile arguments.                                                                                                                                                                                                             |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Switch Build Target

Changes build target of the project

#### Input Fields

| Field        | Required | Description               |
| ------------ | -------- | ------------------------- |
| Build Target | Yes      | *no description provided* |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---


## Control Flow

### ELSE

Executes child steps if prior condition returned false.

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Exit Scope

Exits a current scope

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### IF

If conditions are true, then child Steps are executed.

#### Input Fields

| Field      | Required | Description                                                  |
| ---------- | -------- | ------------------------------------------------------------ |
| Conditions | Yes      | Conditions that need to be fulfilled to execute child Steps. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Loop

Iterates through each child action.

#### Input Fields

| Field            | Required | Description                                                                |
| ---------------- | -------- | -------------------------------------------------------------------------- |
| Item List        | Yes      | *no description provided*                                                  |
| Iterator Name    | Yes      | Name of the variable which will represent the current item of the loop.    |
| Index Count Name | No       | Name of a variable which will represent the current iteration of the loop. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Repeat

Run child steps specified number of times.

#### Input Fields

| Field              | Required | Description                                                                   |
| ------------------ | -------- | ----------------------------------------------------------------------------- |
| Repeat Count       | No       | Number of times to repeat sub-steps.                                          |
| Repeat Number Name | Yes      | Name of the variable which will be resolved as current repeat count.          |
| Start At Zero      | Yes      | Whether or not to start count at zero (the repeat count will offset as well). |
| Reverse            | Yes      | Supplied value will be decremented instead of incremented.                    |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Stop Job

Stops a currently running job.

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### While

Iterates through each child action while condition is true.

#### Input Fields

| Field            | Required | Description                                                                |
| ---------------- | -------- | -------------------------------------------------------------------------- |
| Conditions       | Yes      | Conditions that need to be fulfilled to execute child Steps.               |
| Index Count Name | No       | Name of a variable which will represent the current iteration of the loop. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---


## Editor Prefs

### Delete All EditorPrefs

Deletes all EditorPrefs keys and their values.

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Delete EditorPrefs

Deletes an EditorPrefs key and its value.

#### Input Fields

| Field | Required | Description                               |
| ----- | -------- | ----------------------------------------- |
| Key   | Yes      | Key which identifies an editor pref item. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Get EditorPrefs (float)

Gets the value of preference by identified key.

#### Input Fields

| Field | Required | Description                               |
| ----- | -------- | ----------------------------------------- |
| Key   | Yes      | Key which identifies an editor pref item. |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |
| Return Value | Value which is returned from EditorPrefs.                 |

---

### Get EditorPrefs (boolean)

Gets the value of preference by identified key.

#### Input Fields

| Field | Required | Description                               |
| ----- | -------- | ----------------------------------------- |
| Key   | Yes      | Key which identifies an editor pref item. |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |
| Return Value | Value which is returned from EditorPrefs.                 |

---

### Get EditorPrefs (integer)

Gets the value of preference by identified key.

#### Input Fields

| Field | Required | Description                               |
| ----- | -------- | ----------------------------------------- |
| Key   | Yes      | Key which identifies an editor pref item. |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |
| Return Value | Value which is returned from EditorPrefs.                 |

---

### Get EditorPrefs (string)

Gets the value of preference by identified key.

#### Input Fields

| Field | Required | Description                               |
| ----- | -------- | ----------------------------------------- |
| Key   | Yes      | Key which identifies an editor pref item. |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |
| Return Value | Value which is returned from EditorPrefs.                 |

---

### Set EditorPrefs (float)

Sets the value of preference by identified key.

#### Input Fields

| Field     | Required | Description                               |
| --------- | -------- | ----------------------------------------- |
| Key       | Yes      | Key which identifies an editor pref item. |
| New Value | Yes      | New Value of EditorPrefs key.             |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |

---

### Set EditorPrefs (boolean)

Sets the value of preference by identified key.

#### Input Fields

| Field     | Required | Description                               |
| --------- | -------- | ----------------------------------------- |
| Key       | Yes      | Key which identifies an editor pref item. |
| New Value | Yes      | New Value of EditorPrefs key.             |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |

---

### Set EditorPrefs (integer)

Sets the value of preference by identified key.

#### Input Fields

| Field     | Required | Description                               |
| --------- | -------- | ----------------------------------------- |
| Key       | Yes      | Key which identifies an editor pref item. |
| New Value | Yes      | New Value of EditorPrefs key.             |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |

---

### Set EditorPrefs (string)

Sets the value of preference by identified key.

#### Input Fields

| Field     | Required | Description                               |
| --------- | -------- | ----------------------------------------- |
| Key       | Yes      | Key which identifies an editor pref item. |
| New Value | Yes      | New Value of EditorPrefs key.             |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |

---


## External

### Run Executable

Run any executable and pass arguments to it

#### Input Fields

| Field                | Required | Description                                                                                                           |
| -------------------- | -------- | --------------------------------------------------------------------------------------------------------------------- |
| Executable File Path | Yes      | File path or domain to an executable file.                                                                            |
| Work Directory       | No       | Work directory of an executable                                                                                       |
| Arguments            | No       | Executable arguments                                                                                                  |
| Use Shell Execute    | Yes      | *no description provided*                                                                                             |
| Window Style         | No       | *no description provided*                                                                                             |
| Exit Timeout         | No       | How long to wait (in milliseconds) for the process to finish and exit. Value below 0 means it will wait indefinitely. |
| Kill On Timeout      | No       | Should the process be killed if the timeout period has been exceeded?                                                 |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| Exit Code  | Exit code of the executable.                              |

---

### Run External Job

Runs Job from another Unity project.

#### Input Fields

| Field             | Required | Description                                                                                                           |
| ----------------- | -------- | --------------------------------------------------------------------------------------------------------------------- |
| Unity Exe Path    | Yes      | Path to a unity executable that will be run in batch mode.                                                            |
| Project Path      | Yes      | Path to a project which has a job that will be executed.                                                              |
| Local Job Path    | Yes      | File path to a job that will be executed (relative to target project path).                                           |
| Job Arguments     | No       | Arguments that will be passed to a job execution (do not include dash).                                               |
| Other Arguments   | No       | Additional arguments for Unity executable (must contain dashes to work).                                              |
| Use Shell Execute | Yes      | *no description provided*                                                                                             |
| Window Style      | No       | *no description provided*                                                                                             |
| Exit Timeout      | No       | How long to wait (in milliseconds) for the process to finish and exit. Value below 0 means it will wait indefinitely. |
| Kill On Timeout   | No       | Should the process be killed if the timeout period has been exceeded?                                                 |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| Exit Code  | *no description provided*                                 |

---

## General

### Comment

Places a comment in Job Editor. Doesn't do anything else.

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Group

Groups steps together

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Invoke Menu Item

Runs an action from a menu item

#### Input Fields

| Field          | Required | Description                                                                                                                                   |
| -------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Menu Item Path | Yes      | Path to a Menu Item to execute.<br>E.g. if you want to execute "GameObject > Create Empty", then the path would be "GameObject/Create Empty". |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Make Text List

Makes a list of string items.

#### Input Fields

| Field | Required | Description               |
| ----- | -------- | ------------------------- |
| Items | No       | *no description provided* |

#### Output Fields

| Field        | Description                                               |
| ------------ | --------------------------------------------------------- |
| Is Success   | Returns true if this step has been executed successfully. |
| Result Items | *no description provided*                                 |

---

### Print List

Prints contents of a list, array and anything that implements "IEnumerable".

#### Input Fields

| Field               | Required | Description                                                                                                                    |
| ------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Item List           | Yes      | Item list which contents will be printed out.                                                                                  |
| Type                | Yes      | Type of message which will be logged.                                                                                          |
| Print Unity Console | Yes      | If true, message will be printed into Unity's Console window.                                                                  |
| Flush Immediately   | Yes      | If true, the logs will be saved immediately into a log file (along with pending logs) after this message has been printed out. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Print

Prints a log message to a Unity Console window.

#### Input Fields

| Field             | Required | Description                                                                                                                    |
| ----------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Message           | No       | Message that will be logged.                                                                                                   |
| Type              | Yes      | Type of message which will be logged.                                                                                          |
| Print To Console  | Yes      | If true, message will be printed into RockTomate's Job Session Console window.                                                 |
| Flush Immediately | Yes      | If true, the logs will be saved immediately into a log file (along with pending logs) after this message has been printed out. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Run Job

Runs a local Job

#### Input Fields

| Field      | Required | Description                |
| ---------- | -------- | -------------------------- |
| Target Job | Yes      | Job that will be executed. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Set Variable

Updates the value of a variable

#### Input Fields

| Field                | Required | Description                                                                                             |
| -------------------- | -------- | ------------------------------------------------------------------------------------------------------- |
| Variable Name        | Yes      | Name of the variable which will be affected. Variable identifiers ('%') will be automatically stripped. |
| New Value (required) | Yes      | *no description provided*                                                                               |
| Create New           | Yes      | If true, a new variable will be created with specified value instead of failing the step.               |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Wait

Waits for a specified amount of time.

#### Input Fields

| Field    | Required | Description                              |
| -------- | -------- | ---------------------------------------- |
| Duration | Yes      | Amount of time to wait (in milliseconds) |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Instantiate Prefab

Loads a prefab and instantiates it into a currently active Scene.

#### Input Fields

| Field    | Required | Description                                                                         |
| -------- | -------- | ----------------------------------------------------------------------------------- |
| Prefab   | Yes      | Prefab that will be instantiated.                                                   |
| Position | No       | Starting position of the instantiated GameObject.                                   |
| Name     | No       | Name of the instantiated GameObject (if it's empty then the name won't be altered). |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| GameObject | Instantiated GameObject.                                  |

---


## Git

### Git - Get Repository

Retrives the repository from specified path. This is a required step in order to use other GIT steps.

#### Input Fields

| Field           | Required | Description                                                                                                                     |
| --------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Repository Path | Yes      | Directory path where target repository is located. Specified directory must contain .git. folder to be considered a repository. |

#### Output Fields

| Field      | Description                                                            |
| ---------- | ---------------------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully.              |
| Repository | Repository resource, which is required by other Git steps to function. |

---

### Git - Add Files

Stages files in Git repository

#### Input Fields

| Field          | Required | Description                                                                                                                  |
| -------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Repository     | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                            |
| Files To Stage | Yes      | Array of file paths that will be staged. File paths must be relative to the repository directory path, where `.git` folder is. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Git - Apply Tag

Applies a tag on a specific commit on current branch.

#### Input Fields

| Field         | Required | Description                                                                                                                                                                                                                                |
| ------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Repository    | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                                                                                                                                          |
| Tag Name      | Yes      | Name of the tag.                                                                                                                                                                                                                           |
| Commit Search | No       | Commit onto which tag will be applied.<br>If empty or 0, latest commit will be retrieved.<br>If -N, N to last commit will be retrieved (where N is a number).<br>Alternatively, a commit hash can be supplied directly (searches globally) |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Git - Checkout Branch

Changes local branch.

#### Input Fields

| Field       | Required | Description                                                                       |
| ----------- | -------- | --------------------------------------------------------------------------------- |
| Repository  | Yes      | You need an output value from `Git - Get Repository` step to load the repository. |
| Branch Name | Yes      | Name of the local branch that repository will switch to.                          |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Git - Commit

Commits staged files.

#### Input Fields

| Field      | Required | Description                                                                       |
| ---------- | -------- | --------------------------------------------------------------------------------- |
| Repository | Yes      | You need an output value from `Git - Get Repository` step to load the repository. |
| Message    | Yes      | Commit message.                                                                                  |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Git - Compare Commits

Get file differences between 2 commits of the repository.

#### Input Fields

| Field           | Required | Description                                                                                                                                                                                                                                |
| --------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Repository      | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                                                                                                                                          |
| Commit Search 1 | Yes      | Commit onto which tag will be applied.<br>If empty or 0, latest commit will be retrieved.<br>If -N, N to last commit will be retrieved (where N is a number).<br>Alternatively, a commit hash can be supplied directly (searches globally) |
| Commit Search 2 | Yes      | Commit onto which tag will be applied.<br>If empty or 0, latest commit will be retrieved.<br>If -N, N to last commit will be retrieved (where N is a number).<br>Alternatively, a commit hash can be supplied directly (searches globally) |

#### Output Fields

| Field                 | Description                                                            |
| --------------------- | ---------------------------------------------------------------------- |
| Is Success            | Returns true if this step has been executed successfully.              |
| File Paths            | Array of file paths that were affected (added, deleted, renamed etc.). |
| Added File Paths      | Array of file paths that were added.                                   |
| Deleted File Paths    | Array of file paths that were deleted.                                 |
| Renamed File Paths    | Array of file paths that were renamed.                                 |
| Modified File Paths   | Array of file paths that were modified.                                |
| Conflicted File Paths | Array of file paths which contents are in merge conflict.              |

---

### Git - Create Branch

Creates a new branch.

#### Input Fields

| Field              | Required | Description                                                                                                                                                                                                        |
| ------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Repository         | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                                                                                                                  |
| New Branch Name    | Yes      | Name of the new branch.                                                                                                                                                                                            |
| Checkout Behaviour | Yes      | **On Create Only** - Will checkout to new branch only if it has been successfully created<br>**Always** - Will checkout to specified branch even if it already existed before<br>**Never** - Will never checkout to new branch |

#### Output Fields

| Field          | Description                                               |
| -------------- | --------------------------------------------------------- |
| Is Success     | Returns true if this step has been executed successfully. |
| Branch Created | Whether new branch has been created after this step.      |

---

### Git - Get Branches

#### Input Fields

| Field      | Required | Description                                                                       |
| ---------- | -------- | --------------------------------------------------------------------------------- |
| Repository | Yes      | You need an output value from `Git - Get Repository` step to load the repository. |

#### Output Fields

| Field           | Description                                               |
| --------------- | --------------------------------------------------------- |
| Is Success      | Returns true if this step has been executed successfully. |
| Current Branch  | Name of the currently checked out branch.                 |
| All Branches    | List of all branch names.                                 |
| Remote Branches | List of remote branch names.                                                          |

---

### Git - Get Branch History

Retrieves branch commit history.

#### Input Fields

| Field        | Required | Description                                                                                                       |
| ------------ | -------- | ----------------------------------------------------------------------------------------------------------------- |
| Repository   | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                 |
| Branch Name  | Yes      | Name of the branch which history will be returned.                                                                |
| Commit Count | Yes      | Specifies number of recent commits to return.<br>If 0 or less than 0, the entire commit history will be returned. |

#### Output Fields

| Field          | Description                                                                                                                                                                                                                                                                                                            |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Is Success     | Returns true if this step has been executed successfully.                                                                                                                                                                                                                                                              |
| Commit History | A list of entire commit history.<br>This field returns a list of a Commit instance, which is part of LibGit2Sharp library.<br>You can explore [its source code](https://github.com/libgit2/libgit2sharp/blob/7fc4be5193dbdd08538b4b150332b5a73770e0f6/LibGit2Sharp/Commit.cs) to find out about its properties/fields. |

---

### Git - Get Work Directory Files

Get files from the working directory of the repository.

#### Input Fields

| Field              | Required | Description                                                                                               |
| ------------------ | -------- | --------------------------------------------------------------------------------------------------------- |
| Repository         | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                         |
| Retrieve File Type | Yes      | **All** - All affected files will be retrieved.<br>**Staged Only** - Only staged files will be retrieved. |

#### Output Fields

| Field                 | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| Is Success            | Returns true if this step has been executed successfully.             |
| File Paths            | Array of file paths that were affected (added, deleted, renamed etc.) |
| Added File Paths      | Array of file paths that were added.                                  |
| Deleted File Paths    | Array of file paths that were deleted.                                |
| Renamed File Paths    | Array of file paths that were renamed.                                |
| Modified File Paths   | Array of file paths that were modified.                               |
| Conflicted File Paths | Array of file paths which contents are in merge conflict.             |

---

### Git - Init

Initialize a new repository.

#### Input Fields

| Field               | Required | Description                                              |
| ------------------- | -------- | -------------------------------------------------------- |
| New Repository Path | Yes      | Directory path where Git repository will be initialized. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Git - Remove Files

Un-stages files in the target repository.

#### Input Fields

| Field            | Required | Description                                                                                                                       |
| ---------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Repository       | Yes      | You need an output value from `Git - Get Repository` step to load the repository.                                                 |
| Files To UnStage | Yes      | Array of file paths that will be un-staged. File paths must be relative to the repository directory path, where `.git` folder is. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

## I/O

### Copy Directory

Copies directory to a specified destination

#### Input Fields

| Field                 | Required | Description                                                                |
| --------------------- | -------- | -------------------------------------------------------------------------- |
| Source Directory Path | Yes      | Path of the directory that will be copied.                                 |
| New Directory Path    | Yes      | Path to a new directory.                                                   |
| Overwrite             | Yes      | If enabled, the destination copy will be overwritten if it already exists. |
| Excluded Extensions   | No       | Paths which will be excluded.                                              |
| Excluded Paths        | No       | Extensions that will be excluded (e.g. ".meta").                           |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Copy File

Copies file to another destination

#### Input Fields

| Field              | Required | Description                                                                |
| ------------------ | -------- | -------------------------------------------------------------------------- |
| Source File Path   | Yes      | Path to the file which will be copied.                                     |
| New File Copy Path | Yes      | Destination file path.                                                     |
| Overwrite          | Yes      | If enabled, the destination copy will be overwritten if it already exists. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Create Directory

Creates an empty directory

#### Input Fields

| Field          | Required | Description                          |
| -------------- | -------- | ------------------------------------ |
| Directory Path | Yes      | Path where directory will be created |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Delete Directory

Deletes a directory

| Field          | Required | Description                                |
| -------------- | -------- | ------------------------------------------ |
| Directory Path | Yes      | Path of a directory which will be deleted. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Delete File

Deletes a file

#### Input Fields

| Field     | Required | Description                          |
| --------- | -------- | ------------------------------------ |
| File Path | Yes      | Path of a file which will be deleted |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Move Directory

Moves directory from one place to another. Creates a destination directory if it doesn't exist.

#### Input Fields

| Field                 | Required | Description                                                                                         |
| --------------------- | -------- | --------------------------------------------------------------------------------------------------- |
| Source Directory Path | Yes      | Path to the directory which will be moved.                                                          |
| Destination Directory | Yes      | Directory to where the directory will be moved to.                                                  |
| Overwrite             | Yes      | If enabled, directories with duplicate contents will be overwritten. Otherwise, it will be skipped. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Move File

Moves file from one place to another. Creates a destination directory if it doesn't exist.

#### Input Fields

| Field                 | Required | Description                                                                                      |
| --------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| Source File Path      | Yes      | Path to the file which will be moved.                                                            |
| Destination File Path | Yes      | New file path of the source file.                                                                |
| Overwrite             | Yes      | If enabled, duplicate file in destination folder will be deleted. Otherwise, it will be skipped. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Open File/Folder

Opens a file/folder with a default program.

#### Input Fields

| Field | Required | Description                                       |
| ----- | -------- | ------------------------------------------------- |
| Path  | Yes      | Path to a file or directory which will be opened. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Rename Directory

Renames a specified directory

#### Input Fields

| Field              | Required | Description                               |
| ------------------ | -------- | ----------------------------------------- |
| Directory Path     | Yes      | Path to a directory that will be renamed. |
| New Directory Name | Yes      | New name for the directory.               |

#### Output Fields

| Field              | Description                                               |
| ------------------ | --------------------------------------------------------- |
| Is Success         | Returns true if this step has been executed successfully. |
| New Directory Path | Returns a path to a new directory.                        |

---

### Update Text File

Updates contents of a text file (or creates a new one if it doesn't exist).

#### Input Fields

| Field                    | Required | Description                                                       |
| ------------------------ | -------- | ----------------------------------------------------------------- |
| File Path                | Yes      | Path to a file that will be affected.                             |
| Contents                 | No       | Contents of the new file.                                         |
| Write Mode               | No       | Whether to add a newline at the end an individual content or not. |
| Duplicate File Behaviour | No       | Specifies what to do if file already exists.                      |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

## Network

### Download from URL

Downloads a file from a given URL.

#### Input Fields

| Field                 | Required | Description                                                                                                                                                                                                                                              |
| --------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| URL                   | Yes      | URL to download files from.                                                                                                                                                                                                                              |
| Destination File Path | Yes      | Destination directory where downloaded file will be placed.                                                                                                                                                                                              |
| Redirect Limit        | No       | Indicates the number of redirects which this request will follow before halting with a “Redirect Limit Exceeded” system error. If you do not wish to limit the number of redirects, you may set this property to any negative number. (NOT RECOMMENDED). |
| Use Chunked Transfer  | Yes      | Indicates whether the `UnityWebRequest` system should employ the HTTP/1.1 chunked-transfer encoding method.                                                                                                                                                |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Submit Web Request

Submits a web request.

#### Input Fields

| Field        | Required | Description                                |
| ------------ | -------- | ------------------------------------------ |
| Request Type | Yes      | Type of request.                           |
| URL          | Yes      | Destination where request will be sent to. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---


## Scene

### Close Scene

Closes a scene from the editor.

#### Input Fields

| Field  | Required | Description                                                           |
| ------ | -------- | --------------------------------------------------------------------- |
| Scene  | Yes      | Scene which will be unloaded.                                         |
| Remove | Yes      | Whether or not should the scene be removed from the Hierarchy window. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Create GameObject

TODO

---

### Delete GameObject

TODO

---

### Find GameObjects

TODO

---

### Open Scene

Opens a target unity scene in editor.

#### Input Fields

| Field      | Required | Description                                              |
| ---------- | -------- | -------------------------------------------------------- |
| Scene      | Yes      | Scene which will be opened.                              |
| Scene Mode | Yes      | Specify how scene should be opened.                      |
| Set Active | Yes      | Whether or not to set the scene active when it's opened. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Save Scenes

Saves all open unity scenes.

#### Input Fields

*none*

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Set Scene Active

Sets a specified scene as active. Note that it must be loaded.

#### Input Fields

| Field | Required | Description                        |
| ----- | -------- | ---------------------------------- |
| Scene | Yes      | Scene which will be set to active. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---


## String

### Append to String

Appends a string to another string

#### Input Fields

| Field       | Required | Description                               |
| ----------- | -------- | ----------------------------------------- |
| String      | Yes      | String to append to                       |
| New Strings | Yes      | Strings to append to the original string. |
| Add Newline | Yes      | Adds a newline before appending string.   |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| Output     | Result string.                                            |

---

### String Contains

Checks if string contains a specified string/character

#### Input Fields

| Field                  | Required | Description                                                                              |
| ---------------------- | -------- | ---------------------------------------------------------------------------------------- |
| String                 | Yes      | String which will be searched.                                                           |
| Text                   | Yes      | Text which will be searched. Serves as a pattern if 'Use Regex' option is enabled.       |
| Use Regex              | Yes      | If true, then text will be searched based on regex.                                      |
| String Comparison Mode | Yes      | Comparison mode used when comparing strings (not used if 'Use Regex' option is enabled). |
| Regex Options          | Yes      | Regex Options (not used if 'Use Regex' option is disabled).                              |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### String Replace

Replaces a part of string with another string

#### Input Fields

| Field     | Required | Description                                           |
| --------- | -------- | ----------------------------------------------------- |
| String    | Yes      | Input string                                          |
| Old Value | Yes      | A string to be replaced                               |
| New Value | Yes      | A string to replace all occurrences of the old value. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| Output     | Result string                                                          |

---

### Trim String

Trims a String

#### Input Fields

| Field      | Required | Description                                                                                                                                                                                       |
| ---------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| String     | Yes      | String to be trimmed                                                                                                                                                                              |
| Trim Chars | No       | Characters that will be trimmed (whitespace by default).                                                                                                                                          |
| Trim Mode  | Yes      | How will a string be trimmed<br>**Default** - trims both beginning and trailing parts<br>**Trim Start** - only beginning part will be trimmed<br>**Trim End** - only ending part will be trimmed. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |
| Output     | Result string                                                          |

---


## ZIP

### Compress to ZIP

Compresses directory files to a ZIP archive

#### Input Fields

| Field            | Required | Description                                                                                                                     |
| ---------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Output Path      | Yes      | Output file path of an exported ZIP file.                                                                                       |
| Target Directory | Yes      | Directory that will be compressed into a ZIP.                                                                                   |
| Put In Directory | Yes      | If enabled, source files are placed into root folder inside of archive. Root Folder will be named after the outputted ZIP file. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---

### Extract ZIP

Extracts contents of a ZIP archive file into target directory

#### Input Fields

| Field                 | Required | Description                                                                     |
| --------------------- | -------- | ------------------------------------------------------------------------------- |
| Zip Path              | Yes      | Path to a ZIP archive file that will be extracted.                              |
| Output Directory Path | Yes      | Path to a directory which will hold extracted files.                            |
| Overwrite Files       | Yes      | If true, extracted files will overwrite existing files in the Output Directory. |

#### Output Fields

| Field      | Description                                               |
| ---------- | --------------------------------------------------------- |
| Is Success | Returns true if this step has been executed successfully. |

---