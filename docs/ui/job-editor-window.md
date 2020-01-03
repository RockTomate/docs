---
id: job-editor-window
title: Job Editor Window
---

![](/products/rocktomate/assets/ui/job-editor-window.png)

Job Editor Window is the main part of RockTomate: this is where most time is spent editing Job and running Jobs.

When instantiated, the window gets auto-docked next to [Game](https://docs.unity3d.com/Manual/GameView.html) or [Scene](https://docs.unity3d.com/Manual/UsingTheSceneView.html) windows if they're present.

## Toolbar

At the top, the window displays a relative path to a Job which is currently being edited.

### Steps

Opens [Step Browser Window](ui/step-browser-window.md).

### Variables

Opens [Variable Manager Window](ui/variable-manager-window.md).

### Logs

Opens [Job Session Logs Window](ui/job-session-logs-window.md).

### Expand/Collapse All

Expands/Collapses all steps that have child steps.

### Play

Begins the execution of a currently edited Job.

### Stop

Interrupts the execution of a currently executing Job. 

Note that sometimes the operation may not be possible depending on the nature of the Job. For example, when building a project, a progress bar appears which blocks input on background UI including RockTomate's Job Editor Window. There is now workaround for this.

## Columns

| Column      | Description                                               |
|-------------|-----------------------------------------------------------|
| *empty*     | Specifies row number (can be hidden by right-clicking it) |
| Description | Step description. Contains the name and its description.  |
| Enabled     | Whether or not the step has been enabled                  |
| Suppressed  | Whether to continue execution if step failed              |
| Status      | Current status of the step                                |

## Managing Steps

Editor lists all Steps in a tree-view fashion. Steps that accept children are nested within one another.

### Deleting Step

*After selecting a desired Step.*

Menu item: "Delete"  
Shortcut: `Delete` key

### Re-order Step

*After selecting a desired Step.*

Menu item: "Move Up" or "Move Down"
Shortcut: `Shift + ↑` or `Shift + ↓`

Also can be reordered by simply dragging them around.

### Duplicate Step

*After selecting a desired Step.*

Menu item: "Duplicate"  
Shortcut: `Shift + D`

### Enable/Disable Step

*After selecting a desired Step.*

Shortcut: `F2`  
Or can be disabled by toggling checkbox in a "Enabled" column.

## Behaviour

### Runtime

![](/products/rocktomate/assets/ui/job-editor-window-runtime.png)

The window turns orange to indicate that the Job started running. You can't edit or select anything. 

A currently executed step will be automatically selected and followed if it's outside the visibility area.