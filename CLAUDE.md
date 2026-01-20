# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AnnouncerTool is a Windows Forms GUI application for creating Announcers MOD for the game LobotomyCorp. It parses folder structures, generates expected image/sound filenames from text tags, and can optionally generate placeholder PNG files.

**Target Framework**: .NET 8.0 Windows
**UI Framework**: Windows Forms
**Language**: C# with implicit usings and nullable reference types enabled

## Build Commands

```bash
# Build release version
dotnet build -c Release

# Build debug version
dotnet build

# Run the application
dotnet run
```

## Project Structure

- [Program.cs](Program.cs) - Application entry point with STAThread for Windows Forms
- [MainForm.cs](MainForm.cs) - Main GUI form containing all application logic
- [AnnouncerTool.csproj](AnnouncerTool.csproj) - Project file with Windows Forms and COM reference configuration
- [Announcer.ico](Announcer.ico) - Application icon

## Architecture

### Single-File Design
The entire application logic is contained in [MainForm.cs](MainForm.cs), which includes:
- **Announcer class** (lines 10-25): Data model for announcer entries with properties for Name, BorderColor, Random, Quantity, Expression, multilingual texts, and image assignments
- **MainForm class** (lines 27-805): Complete UI and business logic

### Data Model
- **Tags**: 16 predefined announcement event types (Click, StartWork, HalfOverWork, OverWork, AgentDie, etc.)
- **Multi-language support**: Dictionary structure `language -> tag -> text`
- **Image assignments**: Maps tags to source PNG file paths
- **Variant system**: Tags can have numbered variants (e.g., `AgentDie_TEXT_1`, `AgentDie_TEXT_2`) controlled by Quantity property

### Key Workflows

1. **Tag Renumbering** ([RenumberTags](MainForm.cs#L237-L364)): When Quantity changes, automatically converts between single tags and numbered variants while preserving text and image assignments

2. **Mod Export** ([SaveMod](MainForm.cs#L572-L659)):
   - Creates `AnnouncersImage_LEB/` folder with PNG files
   - Creates `AnnouncersTEXT_LEB/{AnnouncerName}/{language}/` folders with XML files
   - Generates `AnnouncersXML_LEB.xml` root configuration
   - Copies assigned images, renaming from tag format to game-expected format (e.g., `Click_TEXT` → `AnnouncerClick.png`)

3. **Mod Import** ([LoadExistingMod](MainForm.cs#L661-L757)): Loads existing `AnnouncersXML_LEB.xml` and reconstructs announcer data from folder structure

### COM Reference
The project includes a COM interop reference (GUID `215d64d2-031c-33c7-96e3-61794cd1ee61`) used by Microsoft.VisualBasic for the InputBox dialog ([AddLanguage](MainForm.cs#L501)).

## Output Format

The tool generates a mod structure compatible with LobotomyCorp Announcers MOD:
```
{SaveFolder}/
├── AnnouncersXML_LEB.xml
├── AnnouncersImage_LEB/
│   └── {AnnouncerName}/
│       ├── Announcer.png
│       ├── UI.png
│       └── Announcer{TagName}.png (for each assigned tag)
└── AnnouncersTEXT_LEB/
    └── {AnnouncerName}/
        └── {language}/
            └── {language}.xml
```

## Important Implementation Details

- **Image handling**: Uses System.Drawing.Common (version 7.0.0) for image operations
- **XML generation**: Uses System.Xml.Linq with UTF-8 encoding
- **Tag format conversion**: Removes `_TEXT` suffix when converting to image filenames (line 620)
- **Placeholder generation**: [CreatePlaceholderPng](MainForm.cs#L791) creates 512x512 gray placeholder images when needed
- **State management**: Uses `isUpdatingAnnouncerSelection` flag to prevent event loops during UI updates
- **Custom drawing**: ListBox uses owner-draw mode to gray out empty tags ([LstTags_DrawItem](MainForm.cs#L530))
