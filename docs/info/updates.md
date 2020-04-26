---
id: updates
title: Update History
---

---

## 1.0.3 (14 May, 2020)

> Macro folder Hierarchy has changed. You need to delete "Macros" directory located inside 'RockTomate/Scripts/' before updating.

### Changes & Improvements
- RockTomate settings are now stored in "ProjectSettings" directory
- Can now copy job variable values to clipboard (evaluates formulas as well)
- [Step Browser] All categories are now sorted in alphabetical order
- Added additional user settings in the "Preferences" window
- [Formula] A string type is no longer assumed to be a collection type. This means that RockTomate won't attempt to iterate over every character of a string but instead iterate once, returning the whole string in the process.
- [Job Editor] Dragging a Job asset now automatically creates a "Run Job" step with a dragged Job assigned
- Job Session Log has been renamed to "Job Session Console"
- [Job Session Console] Can now filter out specific log entries (shows main ones by default)
- [Job Session Console] Can now sort log entries by Type
- [Job Session Console] Double-clicking on a log entry  auto-focuses a related Step
- [Job Session Console] Now automatically scrolls to the bottom by default
- [Job Session Console] Log entries are now color coded by type to be easily identifiable
- [Job Session Console] Removed unusable expand all/collapse all buttons
- [Job Session Console] Added option to clear log entries from the window
- [Job Session Console] Step row number is now a separate column instead of being printed along with a message
- [Job Session Console] Hovering over a message will display the full message


### Root Variables
- Added: `%UnityDir%`
- Added: `%IsTempProject%`
- Added: `%AppVersion%`
- Added: `%IsBuilding%`
- Added: `%IsCompiling%`
- Added: `%TimeSinceStartup%`
- Added: `%HasCompilationErrors%`


### Macros
- Added: `trim()`
- Added: `starts_with()`
- Added: `ends_with()`


### Steps
- New Plugin Integration: [P.A.T.C.H](https://assetstore.unity.com/packages/tools/utilities/p-a-t-c-h-ultimate-patching-system-41417)
- New Plugin Integration: [Bakery GPU Lightmapper](https://assetstore.unity.com/packages/tools/level-design/bakery-gpu-lightmapper-122218)
- New Plugin Integration: [SG Patcher](https://assetstore.unity.com/packages/tools/utilities/sg-patcher-simple-assetbundles-alternative-163468)
- Added: Print List
- Added: Copy Asset
- Added: Delete Asset
- Added: Create ScriptableObject Asset
- Added: Comment
- [Compile DLL] Fixed issues when trying to compile scripts in Unity 2019.3 or later
- [Print] Now prints to Unity Console by default. Printing to Job Session Console is now optional


### Bug fixes
- [Job Session Console] Fixed a bug when would sometimes throw exceptions
- Fixed a bug when duplicating a "Run Job" step would throw errors
- [Variable Bank Editor] Fixed a bug when changes wouldn't be saved when window is closed
- Fixed a bug when nested macros would sometimes fail
- Fixed a bug when formulas like `split("Hello, world", ',')` wouldn't parse
- Fixed a bug when duplicating a Job asset file would also duplicate its unique Id
- Fixed a bug when custom step drawers wouldn't be utilized

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

### Root Variables
- New root variable: `%CompileSymbols%`
- New root variable: `%IsOnline%`

### Macros
- New input macro: `contains(%array%, %item%)` - checks if array contains an item
- New input macro: `pretty(%string%)` - prettifies a string (adds space between capital letters)
- New input macro: `invert(%boolean%)` - inverts a boolean
- New output macro: `invert(%boolean%)` - inverts a resultant boolean and saves it to a variable

### Steps
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

### Steps

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

## 1.0.0 (1 January, 2020)

🎂 Initial release