---
id: updates
title: Update History
---

## 1.1.4 (TBD, 2021)

> Due to the changes in the project hierarchy, the current version of RockTomate must be removed before the new one could be imported.<br><br>
> Your existing jobs will be unaffected.

> You may notice that steps in your existing jobs will have a status of "Unknown". This is completely normal and will be gone after you run jobs at least once.

### Changes & Improvements

#### Documentation
- Macros Wiki on GitHub has been deprecated and is no longer being maintained. All content has been migrated to [Macro References](/references/macro-references) page.
- Steps Wiki on GitHub has been deprecated and is no longer being maintained. All content has been migrated to [Step References](/references/step-references) page.

#### General
- Added support for Unity 2021.2
- [Editor] Miscellaneous performance and optimization improvements
- [Editor] Disabling a Step now shows a warning message in Step Properties window. You can disable this behaviour in `Preferences > RockTomate > Show Step Disabled Warning`
- [Editor] Can now quickly open Step's .cs file from Step Properties window. This option is turned off by default and can be found in `Preferences > RockTomate > Show Step Script Field`
- [Editor] Added a scroll when dealing with large lists in variable list editor window
- [Job Session Console] Added a preference option to print Job Session console messages to Unity console window as well
- Can now mark Steps' input fields as "sensitive", which hides their output value in log messages
    - *this feature is brand new so please still check your log messages that you share with public. If you think some sensitive info is still leaking please let me know*
- RockTomate now stores session data in "Library/RockTomateCache" directory

#### Steps
- [Build Player] Specifying file path in the `Output Path` field will now override the `File Name` and won't append an extension. This was done to ensure backwards compatibility with older configurations made  before version `1.1.3`
- [Upload to Asset Store] Marked `Username` and `Password` fields as sensitive
- [Build Asset Bundles] Added a missing compression option: `Standard LZMA`, which is now a default option

#### Macros
- Added: [`merge()`](/references/macro-references#merge)

### Bug fixes

#### General
- [Job Editor] Fixed a bug when editing Job or its Step properties wouldn't mark it as dirty reliably

#### Variables
- Fixed a bug when Variable Banks did not respect "keep persistent" setting and would save values regardless

#### Steps
- [Run Job] No longer fails when trying to run a "Loop" step in sub-Job
- [Run Job] Fixed a bug when step is marked as successful even if sub-job failed
- [Run Job] Fixed a bug when step is marked as failed if one of the steps in sub-job has failed but is marked as "suppressed"
- [Build Asset Bundles] Now correctly applies `Chunk Based` and `Uncompressed` options to asset bundles

---

## 1.1.3 (24 May, 2021)

### Changes & Improvements

#### General
- Added support for Unity 2020.3
- Added support for Unity 2021.1
- Event manager data file is now required to be manually assigned instead of being auto-created on project initialisation.
- Added a shortcut option to stop a currently running RockTomate job.

#### Variables
- Can now create and edit array-type variables

#### Steps
- [Build Player] Added `File Name` field to ask for exported file name where needed. Extension will be appended depending on the chosen platform.
    - *to clarify, the `Output Path` field is for folder output path and will always be required*
- [Build Player] Now checks if the Build Target is supported by a currently running Unity engine
- [Create GameObject] Now passes created game object as an output field

#### Macros
- Added: `is_empty()`
- Added: `join()`

#### Root Variables
- Added: `%IncludedScenesInBuild%`
- Added: `%AllScenesInBuild%`
- `%ScriptingRuntimeVersion%` is no longer available in Unity versions 2019.3 and later as it's been deprecated

### Bug fixes

#### General
- Fixed one-time compilation errors occurring when importing RockTomate for the first time

#### Variables
- Fixed a bug when variables that have formulas enabled would be modified when copying resolved value to clipboard

#### Steps
- [Create GameObject] Fixed a bug when step would create 2 same GameObjects instead of one
- [Set Variable] Fixed an error if variable was not found when "Create New" option is disabled
- [Run Job] Fixed a bug when formulas wouldn't be correctly resolved when overriding job variables

---

## 1.1.2 (1 March, 2021)

> This version introduces a new dependency: [**LibGit2Sharp**](https://github.com/libgit2/libgit2sharp)

### Changes & Improvements

#### General
- Can now run Jobs via [shortcuts](/workflows/running-job#running-using-shortcuts) (Unity 2019.1 or newer)
- Memory management improvements

#### Job Editor Window
- Can now open recent jobs when no job has been selected
- Disabled "Run This" option for Comment steps

#### Step Browser Window
- Improved search algorithm

#### Step Properties Window
- Field types that have generics (e.g. `List<string>`) are now displayed correctly in tooltips

#### Variable Manager Window
- Can now reorder variables

#### Variable Bank Editor Window
- Can now reorder variables

#### Steps
- Added: Run Unit Tests (requires [`com.unity.test-framework`](https://docs.unity3d.com/Packages/com.unity.test-framework@1.1))
- Added 12 Git-related steps (.NET 4.6 or newer):
    - Init
    - Add
    - Remove
    - Commit
    - Apply Tag
    - Get Repository
    - Get Branches
    - Get Branch History
    - Get Work Directory Files
    - Compare Commits
    - Create Branch
    - Checkout Branch
- [Print List] Fixed an issue when trying to print with an empty list would fail this Step
- [Run Job] Added "Auto Run" option
- [Build Player] Added "Manual Cancel Fails Step" option (enabled by default). Cancelling building process manually will no longer mark Step as successful by default.

#### Macros
- Added: `peel()`
- Added: `is_git_repo()`
- Added: `get_git_last_commit_hash()`
- Added: `get_git_current_branch()`

#### Root Variables
- Added: `%ScriptableRuntimeVersion%`
- Added: `%IsGitRepo%`
- Added: `%GitLastCommitHash%`
- Added: `%GitCurrentBranch%`

### Bug fixes

#### General
- Fixed a bug when RockTomate's preferences could not be edited and `SerializedObject target has been destroyed` error being printed all the time
- Fixed a bug when formula icons wouldn't render properly (Unity 2020.1 or newer)

#### Job Editor Window
- Fixed a bug when opening a Job wouldn't focus the window if it's already been opened before 

#### Step Browser Window
- Fixed a bug when step list items wouldn't render properly (Unity 2020.1 or newer)

---

## 1.1.1 (13 January, 2021)

### Changes & Improvements

#### General

- [Job Editor Window] Improved performance when large Jobs with lots of steps are rendered
- Added support for Unity 2020.2
- Upgraded Odin Serializer version
- New Step status: `Unknown`. If you see it, that means there was an internal error when trying to retrieve Step's status. Keep an eye out for it and if you see it, report it.

### Bug fixes

#### General
- Fixed serialization issues when trying to run Steps that have fields of type `Unity.Object`
- Fixed a bug that caused Unity to freeze occasionally when duplicating Jobs or Variable Banks (using `CTRL/CMD + D` shortcut command)
- Fixed a bug that caused Unity to freeze occasionally when starting a project
- Fixed a bug when menu item at `Tools > RockTomate > Utils > Open Directory > Project Root` wouldn't open root of the project directory

---

## 1.1.0 (1 October, 2020)

### Changes & Improvements

#### General
- Added Event Manager - allows you to configure RockTomate to automatically run jobs if certain events happen (e.g. new asset gets imported into project)
- [Variable Manager] Persistent variables - persist variable values between job executions
- [Variable Manager] Added new variable type: "Version"
- Added support for Unity 2019.4
- Added support for Unity 2020.1
- RockTomate Jobs progress is now visible in the "Background Tasks" window (Unity 2020.1 or newer)
- Can now run Job from the Inspector Window when it's selected
- [Condition Editor Control] Minor GUI tweaks
- [Job Editor Window] Can now quickly open previous Job files
- [Formula] Can now run multiple macros in a single formula (not just nested) using [String Interpolation](../formulas/string-interpolation.md)

#### Root Variables
- Added: `%LibraryDir%`

#### Macros
- Added: `if()`
- Added: `envar()`
- Added: `asset_type()`
- Added: `incr()`
- Added: `decr()`

### Bug fixes

#### General
- [General] Fixed a bug when Unity would freeze when running a Job at random times
- [Step Browser Window] Fixed an error when double-clicking on a Step while Job Editor is not visible
- [Variable Bank Window] Fixed a bug when variables wouldn't be created correctly when Job Editor didn't have any Jobs to edit
- [Variable Manager Window] Fixed a bug when you couldn't drag first variable bank into "External" tab

---

## 1.0.3 (21 May, 2020)

> Due to the changes in the project hierarchy, the current version of RockTomate must be removed before the new one could be imported.<br><br>
> Your existing jobs will be unaffected.

### Changes & Improvements

#### General
- [Job Editor] Can now run a single Step
- RockTomate settings are now stored in "ProjectSettings" directory
- Can now copy job variable values to clipboard (evaluates formulas as well)
- [Step Browser] All categories are now sorted in alphabetical order
- Added additional user settings in the "Preferences" window
- Job Session Log has been renamed to "Job Session Console"
- [Job Session Console] Can now sort log entries by Type
- [Job Session Console] Log entries are now color coded by type to be easily identifiable
- [Job Session Console] Removed unusable expand all/collapse all buttons
- [Job Session Console] Can now clear console window
- Printed log entries give more information regarding the failed jobs
- RockTomate related log entries are automatically printed out if Unity is running in Batch Mode
- Added an option to clear cache directory and log entries (available in `Tools > RockTomate > Utils > Clear` menu option)

#### Root Variables
- Added: `%UnityDir%`
- Added: `%IsTempProject%`
- Added: `%AppVersion%`
- Added: `%IsBuilding%`
- Added: `%IsCompiling%`
- Added: `%TimeSinceStartup%`

#### Macros
- Added: `trim()`
- Added: `starts_with()`
- Added: `ends_with()`

#### Steps
- New Plugin Integration: [Bakery GPU Lightmapper](https://assetstore.unity.com/packages/tools/level-design/bakery-gpu-lightmapper-122218)
- Added: Print List
- Added: Copy Asset
- Added: Delete Asset
- Added: Create ScriptableObject Asset
- Added: Comment
- [Print] Now prints to Unity Console by default
- [Print] Added an option to print to Job Session Console (disabled by default)

### Bug fixes

#### General
- [Job Session Console] Fixed a bug when would sometimes throw exceptions
- [Variable Bank Editor] Fixed a bug when changes wouldn't be saved when window is closed
- [Variable Bank Editor] Fixed a bug when Variable Banks created in newer Unity versions would throw null reference exceptions in older Unity versions
- Fixed a bug when creating a variable bank in the "External Tab" would break Run Job's TargetJob Field
- Fixed a bug when whitespace at the end of formula input would skip the formula evaluation stage
- Fixed a bug when nested macros would sometimes fail
- Fixed a bug when formulas like `split("Hello, world", ',')` wouldn't parse
- Fixed a bug when duplicated Job and the original Job would share the same Id, causing errors down the line
- Fixed a bug when custom step drawers wouldn't be utilized

#### Steps
- [Compile DLL] Fixed issues when trying to compile scripts in Unity 2019.3 or later
- [Run Job Step] Fixed a bug when step wouldn't fail if nested Job fails
- [Run Job Step] Fixed a bug when duplication of this step would throw an error
- [Run Job Step] Fixed a bug when exceptions would be thrown for nested Jobs with loop-able steps (e.g. Loop, Repeat etc.)
- [Run Job Step] Fixed a bug when nested Job would continue execution even after parent Job execution has been interrupted

---

## 1.0.2 (14 April, 2020)

### Changes & Improvements
- Minimum version raised to 2018.4.0f1
- Can now rename variables by double-clicking on them or through the context menu
- Can now enable formulas for new fields by default
- Can now disable system sound when Job finishes execution
- Changed context menu items to be less obstructive
- Error message shown if illegal characters are present in variable creation pop-up
- Input field names is now auto-capitalized
- Macro arguments now support single quotes
- RockTomate's temp directory has been moved to Unity's "Temp" directory

#### Root Variables
- New root variable: `%CompileSymbols%`
- New root variable: `%IsOnline%`

#### Macros
- New input macro: `contains(%array%, %item%)` - checks if array contains an item
- New input macro: `pretty(%string%)` - prettifies a string (adds space between capital letters)
- New input macro: `invert(%boolean%)` - inverts a boolean
- New output macro: `invert(%boolean%)` - inverts a resultant boolean and saves it to a variable

#### Steps
- New Steps integration: [Turbo Builder PRO](https://assetstore.unity.com/packages/slug/98714)
- New Steps integration: [Turbo Switch PRO](https://assetstore.unity.com/packages/slug/60040)
- New Steps integration: [Turbo Backup PRO](https://assetstore.unity.com/packages/slug/98711)
- New Steps integration: [Maintainer](https://assetstore.unity.com/packages/slug/32199)
- [Compile DLL] Now auto-creates a missing directory instead of throwing an arbitrary error
- [Upload to Asset Store] Fixed a bug when package would be corrupted

### Bug fixes
- Fixed a bug when existing scripting define symbols would be overwritten
- Fixed a bug when a part of the macro argument would get removed if it either starts or ends with a quote
- Moving RockTomate to a different directory no longer causes UI-related problems
- Creating a directory named "RockTomate" no longer causes UI-related problems
- [Job Editor Window] Fixed an issue when toolbar buttons were clipping in Unity 2019.3 (new UI)
- [Job Editor Window] Fixed an issue when "Suppressed" column label was clipping in Unity 2019.3 (new UI)
- [Variable Manager Window] Fixed an issue when adding an empty variable bank would spam Job Session Log Window with errors
- [Variable Bank Window] Fixed a bug when the variable list wouldn't get updated if different variable bank is selected
- Exceptions are no longer thrown when trying to access "Run Job" step properties window

---

## 1.0.1 (17 March, 2020)

### Changes & Improvements
- Now plays a system sound when Job has finished the execution when Unity isn't in focus
- [Variables Window] Can now copy root variable values to the clipboard (both dynamic and non-dynamic)
- [Variables Window] Root variables that resolve to array/list now show the first 20 items on the list. Copying to the clipboard will return all array items separated by a line.
- [Job Editor Window] Now shows elapsed time while and after running a job.
- Added %WorkDir% root variable - resolves a current working directory of Unity
- Step property fields now properly updated when Step class is modified (e.g. adding or removing a new field etc.)

#### Steps

- New Step: WHILE Loop
- New Step: Upload to Asset Store
- [Move File] Now asks for destination file path, allowing you to rename a file while moving it

### Bug Fixes
- Included Job asset files no longer appear corrupted
- Adjusted visuals to make UI more readable for dark theme users
- Fixed a bug when OR Joining operator would always return true
- Fixed an issue when RockTomate prevented Unity from compiling the game
- Fixed a minor issue where the name of the Job would have "(clone)" appended to it when running through a dialog window.
- Removed unused DLL
- Fixed a bug when child step would get deselected after job changes are saved
- Fixed a bug when it was possible to create new variables while the job was running
- Fixed an exception being thrown when trying to update job metadata when no job is being edited
- Fixed an exception being thrown when trying to start a job with an empty variable bank
- Fixed a bug when maximizing any window would throw errors for other editor windows

---

## 1.0.0 (5 February, 2020)

🎂 Initial release