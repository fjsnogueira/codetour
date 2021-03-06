## v0.0.34 (06/27/2020)

- Updated the tour recorder, to allow you to edit the line associated with a step
- Updated the tour recorder, to allow you to add a tour step from an editor selection
- Added the ability to record a new tour that is saved to an arbitrary location on disk, as opposed to the `.tours` directory of the opened workspace.
- Added new extensibility APIs to record and playback tours for external workspaces (e.g. GistPad repo editing).
- Updated the `CodeTour` tree to always show when you're taking a tour, even if you don't have a workspace open.

## v0.0.33 (06/18/2020)

- Fixed an issue where CodeTour overrode the JSON language type

## v0.0.32 (06/01/2020)

- Added a list of well-known views to the step `view` property (e.g. `scm`, `extensions:disabled`) to simpify the authoring process for view steps.

## v0.0.31 (05/31/2020)

- Exposed the `Add Tour Step` as a context menu to tour nodes in the `CodeTour` tree.
- Update the `CodeTour` tree, so that it doesn't "steal" focus while navigating a tour, if the end-user doesn't have it visible already
- **Experimental** Added the concept of a "view step", which allows you to add a step that automatically focuses a VS Code view and describes it
- **Experimental** Added step commands, which allows a step to include one or more commands that should be executed when the step is navigated to

## v0.0.30 (05/28/2020)

- Changed the `CodeTour` tree to be always visible by default, as long as you have one or more workspaces opened.

## v0.0.29 (05/27/2020)

- Fixed an issue with URI handling on Windows

## v0.0.28 (05/22/2020)

- Introduced support for the step/tour reference syntax.
- Added the following commands to the command link completion list: `Run build task`, `Run task` and `Run test task`.
- Fixed a bug where command links didn't work, if the command included multiple "components" to the name (e.g. `workbench.action.tasks.build`).
- Fixed a bug where tours weren't being discovered for virtual file systems that include a query string in their workspace path.
- Fixed a bug where tours that included content-only steps couldn't be exported.
- Fixed the open/export tour commands to correctly look for `*.tour` files.
- Fixed a bug where the `CodeTour: Record Tour` command was being displayed without having any workspaces open.

## v0.0.27 (05/22/2020)

- Added support for "command links" in your steps, including a completion provider for using well-known commands.
- Improved extension activation perf by building it with Webpack
- Fixed an issue with playing tours for virtual file systems (e.g. `gist://`).

## v0.0.26 (05/17/2020)

- Added support for a codebase to have a "primary" tour, which provides a little more prescription to folks that are onboarding
- Added the `Change Title` command to step nodes in the `CodeTour` tree. This allows you to easily give steps a title without needing to add a markdown header to their description
- Added support for multi-select deletes in the `CodeTour` tree, for both tour and step nodes
- Added a `Preview Tour` command that allows putting the active tour into preview mode
- Updated the tour recorder to automatically place steps into edit mode when you start recording
- The `Save Step` button is now only enabled when recording a step, whose description isn't empty
- Removed the `Start CodeTour` status bar item, which just added noise to the user's statur bar

## v0.0.25 (05/03/2020)

- Introduced the `Add CodeTour Step` context menu to directories in the `Explorer` tree, which allows you to add steps that point at directories, in addition to files.
- Added the `CodeTour: Add Tour Step` command, which allows you to create a content-only step, that isn't associated with a file or directory.
- Fixed a bug where new steps weren't properly focused in the `CodeTour` tree when recording a new tour.

## v0.0.24 (05/02/2020)

- Explicitly marking the `CodeTour` extension as a "workspace extension", since it needs access to the workspace files and Git extension.
- Temporarily removed the `View Notebook` command, since this isn't officially supported in VS Code.

## v0.0.23 (04/19/2020)

- Added the `View Notebook` command to tour nodes in the `CodeTour` tree, which allows you to view a tour as a notebook

## v0.0.22 (04/18/2020)

- New tours are now written to the workspace's `.tours` folder, instead of the `.vscode/tours` folder. Both folders are still valid locations for tours, but the former sets up CodeTour to be more editor-agnostic (e.g. adding a Visual Studio client)
- New tours are now written using a `.tour` extension (instead of `.json`). Both formats are still supported, but `.tour` will be the new default.

## v0.0.21 (04/10/2020)

- Added the `CodeTour: Open Tour URL...` command, that allows opening a tour file by URL, in addition to the existing `CodeTour: Open Tour File...` command.

## v0.0.20 (04/08/2020)

- Introduced support for embedding shell commands in a tour step (e.g. `>> npm run compile`), which allows you to add more interactivity to a tour.
- Added support for including VS Code `command:` links within your tour step comments (e.g. `[Start Tour](command:codetour.startTour)`), in order to automate arbitrary workbench actions.
- Tours can now be organized within sub-directories of the `.vscode/tours` directory, and can now also be places withtin a root-level `.tours` folder.
- Added the `exportTour` to the API that is exposed by this extension

## v0.0.19 (04/06/2020)

- Added support for recording and playing tours within a multi-root workspace
- Added support for recording steps that reference files outside of the currently opened workspace. _Note: This should only be done if the file is outside of the workspace, but still within the same git repo. Otherwise, the tour wouldn't be "stable" for people who clone the repo and try to replay it._
- The `CodeTour` tree now auto-refreshes when you add/remove folders to the current workspace.
- Fixed an issue with "tour markers" being duplicated
- Fixed an issue with replaying tours that were associated with a Git tag ref

## v0.0.18 (04/02/2020)

- Updated the VS Code version dependency to `1.40.0` (instead of `1.42.0`).
- Removed the dependency on the built-in Git extension, to ensure that recording/playback is more reliable.

## v0.0.17 (03/31/2020)

- Introduced "tour markers", which display a gutter icon next to lines of code which are associated with a step in a code tour.

## v0.0.16 (03/30/2020)

- Updated the `CodeTour` tree to display the currently active tour, regardless how it was started (e.g. you open a tour file).

## v0.0.15 (03/29/2020)

- Updated the `CodeTour` tree to only display if the currently open workspace has any tours, or if the user is currently taking a tour. That way, it isn't obtrusive to users that aren't currently using it.
- Updated the `CodeTour: Refresh Tours` command to only show up when the currently opened workspace has any tours.

## v0.0.14 (03/26/2020)

- Added the `Export Tour` command to the `CodeTour` tree, which allows exporting a recorded tour that embeds the file contents needed to play it back
- Added the ability to open a code tour file, either via the `CodeTour: Open Tour File...` command or by clicking the `Open Tour File...` button in the title bar of the `CodeTour` view
- Added support for tour steps to omit a line number, which results in the step description being displayed at the bottom of the associated file

## v0.0.13 (03/23/2020)

- Exposed an experimental API for other extensions to record/playback tours. For an example, see the [GistPad](https://aka.ms/gistpad) extension, which now allows you to create tours associated with interactive web playgrounds

## v0.0.12 (03/21/2020)

- Added a new `Edit Step` command to the `CodeTour` tree, which allows you to start editing a tour at a specific step
- Updated the `CodeTour` tree to only show the move step up/down commands while you're actively recording that step

## v0.0.11 (03/16/2020)

- Updated the `CodeTour` tree to auto-select tree node that is associated with the currently viewing tour step
- Text highlights can now be edited when editing a tour code
- Added support for collapsing all nodes in the `CodeTour` tree
- Added a prompt when trying to record a tour, using a title that is already in use by an existing tour

## v0.0.10 (03/16/2020)

- Introduced support for step titles, which allow defining friendly names for a tour's steps in the `CodeTour` tree
- Exposed an extension API, so that other VS Code extensions (e.g. [GistPad](https://aka.ms/gistpad)) can start and end tours that they manage
- Added the `CodeTour: Edit Tour` command, that allows you to edit the tour you're currently playing.

## v0.0.9 (03/15/2020)

- Added the ability to record a text selection as part of a step

  ![Selection](https://user-images.githubusercontent.com/116461/76705627-b96cc280-669e-11ea-982a-d754c4f001aa.gif)

## v0.0.8 (03/14/2020)

- Added the ability to associate a tour with a specific Git tag and/or commit, in order to enable it to be resilient to code changes
- Updated the tour recorder so that tours are automatically saved upon creation, and on each step/change

## v0.0.7 (03/14/2020)

- Added the `Edit Tour` command to tour nodes in the `CodeTour` tree, in order to allow editing existing tours
- Added the `Move Up` and `Move Down` commands to tour step nodes in the `CodeTour` tree, in order to allow re-arranging steps in a tour
- Added the `Delete Step` command to tour step nodes in the `CodeTour` tree
- Added the ability to insert a step after the current step, as opposed to always at the end of the tour
- Updated the workspace tour notification to display when any tours are available, not just a "main tour"

## v0.0.6 (03/13/2020)

- Added the `'Resume Tour`, `End Tour`, `Change Title`, `Change Description` and `Delete Tour` commands to the `Code Tours` tree view to enable easily managing existing tours
- Added the `Code Tour: End Tour` command to the command palette

## v0.0.5 (03/09/2020)

- Added an icon to the `Code Tours` tree view which indicates the currently active tour
- Added support for creating/replaying tours when connected to a remote environment (thanks @alefragnani!)

## v0.0.4 (03/09/2020)

- Added the save/end tour commands to the `Code Tours` tree view
- The tour file name is now auto-generated based on the specified title

## v0.0.3 (03/08/2020)

- Fixed a bug where recorded tours didn't always save properly on Windows

## v0.0.2 (03/08/2020)

- Added keyboard shortcuts for navigating an active code tour
- Changed the `Code Tours` view to always display, even if the current workspace doesn't have any tours. That way, there's a simple entry point for recording new tours

## v0.0.1 (03/08/2020)

- Initial release 🎉
