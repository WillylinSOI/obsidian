# Note Refactor

![GitHub Workflow Status](https://img.shields.io/github/workflow/status/lynchjames/note-refactor-obsidian/Release%20Build?logo=github&style=for-the-badge)![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/lynchjames/note-refactor-obsidian?style=for-the-badge&sort=semver)

This repository contains a plugin for [Obsidian](https://obsidian.md/) for extracting the selected portion of a notes into new note.

The default hotkeys are:

Hotkey

Action

Ctrl/Cmd + Shift + N

**Extract selection to new note - first line as filename:** Copy selection into new note with the first line as the file name and replace with a link.

Ctrl/Cmd + Shift + C

**Extract selection to new note - content only:** Copy selection into new note, prompt for a file name and replace with a link.

> :warning: Hotkey defaults are deliberately not set for note splitting commands to avoid unwanted accidents.

The new note file is created at the root of the vault with the filename as the first line of the selected text and the content as the rest of the selected text.

Heading characters (`#`) and other illegal characters for filenames are removed including `:`, `\`, `/`.

## Usage

This table shows the different use cases for this plugin and how commands and settings can be used in each case.

### Extracting

Use case

Command

Plugin Settings

1

1. Extract a selection into a new note exactly as it is.  
2. File name for new note provided by the user.

Extract selection to new note - content only

**Include Heading**  
False

2

1. Extract a selection into a new note exactly as it is.  
2. File name for new note set from the first line of the selection

Extract selection to new note - first line as file name

**Exclude First Line**  
False  
  
**Include Heading**  
False

3

1. Extract a selection into a new note.  
2. File name for new note set from the first line of the selection.  
3. First line included in the new note as a heading.

Extract selection to new note - first line as file name

**Exclude First Line**  
False  
  
**Include Heading**  
True

4

1. Extract a selection into a new note  
2. File name for new note set from the first line of the selection.  
3. First line not included in the new note.

Extract selection to new note - first line as file name

**Exclude First Line**  
True  
  

5

1. Extract a selection into a new note exactly as it is.  
2. File name for new note is generated from the **File name prefix** setting.

Extract selection to new note - only prefix as file name

### Splitting

Use case

Command

Plugin Settings

1

1. Split a note from the current line of the cursor into new note exactly as it is.  
2. File name for new note provided by the user.

Split note here - content only

**Include Heading**  
False

2

1. Split a note from the current line of the cursor into new note.  
2. File name for new note provided by the user.  
3. First line included in the new note as a heading.

Split note here - content only

**Include Heading**  
True

3

1. Split a note from the current line of the cursor into new note exactly as it is.  
2. File name for new note set from the first line of the selection.

Split note here - first line as file name

**Include Heading**  
False

4

1. Split a note from the current line of the cursor into a new note.  
2. File name for new note set from the first line of the selection.  
3. First line included in the new note as a heading.

Split note here - first line as file name

**Exclude First Line**  
False  
  
**Include Heading**  
True

5

1. Split a note with content under a heading going into a new note for each heading.  
2. File name for each new note set from the heading.

Split note by headings - H1  
  
Split note by headings - H2  
  
Split note by headings - H3

## Commands

### Note Splitting

Splitting the current note from the current line into a new note or append to an existing one.

#### Split note here - current line as note file name

This command splits the current note into a new note from the current line using the current line as the file name for the new note.

#### Split note here - content only

This command splits the current note into a new note, or append to an existing one, from the current line. The user is prompted to enter a file name for the new note.

#### Split note by headings - H1, H2, H3

This command splits the current note into a new note for every heading at the level selected (H1, H2 or H3) using the heading as the file name for each new note.

![split by headings demo](https://raw.githubusercontent.com/lynchjames/note-refactor-obsidian/master/images/Note-Refactor-Demo-Split-by-Headings.gif)

### Extract Selection

Extracting the current selection into a new note or append to an existing one.

#### Extract selection to new note or append to existing note - first line as filename

This command copies the selected text into the content of a new note using the first line as the file name for the new note or append to an existing one.  
![first line file name demo](https://raw.githubusercontent.com/lynchjames/note-refactor-obsidian/master/images/Note-Refactor-Demo-First-Line-as-File-Name.gif)

#### Extract selection to new note or append to existing note - content only

This command only copies the selected text into the content of a new note or append to an existing one. The user is prompted to enter a file name for the new note.

![content only demo](https://raw.githubusercontent.com/lynchjames/note-refactor-obsidian/master/images/Note-Refactor-Demo-Content-Only.gif)

#### Extract selection to new note - prefix only as file name

This command only copies the selected text into the content of a new note or append to an existing one. The filename is automatically generated based on the value of **File name prefix** setting. New note is created silently and will not be shown in a new pane.

## Configuration

![plugin settings](https://raw.githubusercontent.com/lynchjames/note-refactor-obsidian/master/images/plugin-settings.png)

### Default location for new notes

The location for new notes to be saved as a plugin config setting in line with the Obsidian core `Default location for new notes` setting.

3 options available:

1.  Vault folder
2.  Same folder as current file
3.  Specified folder

The specified folder option allows you to specify a folder path for new notes which can include multiple datetime formats.

**Example**

A folder path set as `Zettels/{{date:YYYY}}/{{date:MMMM}}` will add a new file to the following folder structure:

-   [Vault]
    -   Zettels
        -   2020
            -   October

### File Name Prefix

The file name prefix option allows you to specify a prefix for new notes which can include multiple datetime formats.

**Example**

A prefix set as `{{date:YYYYMMDDHHmm}}-` will add a new file with the following file name:

`202010311425-My New Note`

### Transclude by Default

This config settings means that all inserted internal links to new notes created by any of the extraction or note splitting commands will be added as a transclusion/note embed `![[new note]]` rather than a link `[[new note]]`.

### First Line included as Note Heading

This config setting allows for the first line of the selected text to be included in the new note content as a heading with a configurable heading format `#`, `##`, `###`, etc.

This setting is applied for either the First Line filename or Content Only commands.  
![note heading demo](https://raw.githubusercontent.com/lynchjames/note-refactor-obsidian/master/images/Note-Refactor-Demo-Include-First-Line-as-Note-Heading.gif)

### Note Link Template

This setting sets the template used to generate the content to link to the extracted note. This overrides the Transclude by Default setting.

The following placeholders are supported and will be replaced with dynamic values when the plugin command is exectuted:

-   `{{date}}` the current date, this also supports date and time formats such as `YYYYMMDD` and `HH:mm`.
-   `{{title}}` the title of the original note.
-   `{{new_note_title}}` the title of the new note.
-   `{{new_note_content}}` the refactored content for the new note.

### Refactored Note Template

This setting sets the template used to generate the content for the refactored note.

The following placeholders are supported and will be replaced with dynamic values when the plugin command is exectuted:

-   `{{date}}` the current date, this also supports date and time formats such as `YYYYMMDD` and `HH:mm`.
-   `{{title}}` the title of the original note.
-   `{{new_note_title}}` the title of the new note.
-   `{{new_note_content}}` the refactored content for the new note.

## Compatibility

Custom plugins are only available for Obsidian v0.9.7+.

The current API of this repo targets Obsidian **v0.9.10**.