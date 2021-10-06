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
---

### Run External Job
---

## General

### Comment
---

### Group
---

### Invoke Menu Item
---

### Make Text List
---

### Print List
---

### Print
---

### Run Job
---

### Set Variable
---

### Wait
---

### Instantiate Prefab
---


## Git

### Git - Get Repository
---

### Git - Add Files
---

### Git - Apply Tag
---

### Git - Checkout Branch
---

### Git - Commit
---

### Git - Compare Commits
---

### Git - Create Branch
---

### Git - Get Branches
---

### Git - Get Branch History
---

### Git - Get Work Directory Files
---

### Git - Init
---

### Git - Remove Files
---

## I/O

### Copy Directory
---

### Copy File
---

### Create Directory
---

### Delete Directory
---

### Delete File
---

### Move Directory
---

### Move File
---

### Open File/Folder
---

### Rename Directory
---

### Update Text File
---

## Network

### Download from URL
---

### Submit Web Request
---


## Scene

### Close Scene
---

### Create GameObject
---

### Delete GameObject
---

### Find GameObjects
---

### Open Scene
---

### Save Scenes
---

### Set Scene Active
---


## String

### Append to String
---

### String Contains
---

### String Replace
---

### Trim String
---


## ZIP

### Compress to ZIP
---

### Extract ZIP
---
