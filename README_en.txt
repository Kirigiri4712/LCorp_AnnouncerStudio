================================================================================
                        Announcer Creator Tool
                    For Lobotomy Corporation MODs
================================================================================

A GUI tool for creating Announcer MODs for Lobotomy Corporation.

--------------------------------------------------------------------------------
                            QUICK START
--------------------------------------------------------------------------------

1. Launch AnnouncerTool.exe
2. Click "Add" button next to Language to add a language code (e.g., "en", "jp")
3. Edit announcement text for each tag in the list
4. Assign Announcer.png (512x512) and UI.png (345x213) images
5. Select a save folder and click "Save Mod"
6. Copy the generated folder to your Lobotomy Corporation mods directory

--------------------------------------------------------------------------------
                         REQUIREMENTS
--------------------------------------------------------------------------------

- Windows 10/11 (64-bit)
- .NET 8.0 Runtime (included in self-contained build)

--------------------------------------------------------------------------------
                         INSTALLATION
--------------------------------------------------------------------------------

1. Extract the zip file to any folder
2. Ensure the "Languages" folder is in the same directory as the exe
3. Run AnnouncerTool.exe

--------------------------------------------------------------------------------
                        DETAILED USAGE
--------------------------------------------------------------------------------

=== Creating a New Announcer ===

1. Launch the tool - a default announcer "NewAnnouncer1" is created
2. Enter the announcer name in the text field (English characters recommended)
3. Click "Add" next to Language to add a language code (e.g., "jp", "en", "kr")
4. Tags will be automatically generated based on your settings
5. Click each tag in the list to edit its announcement text

=== Tag Descriptions ===

| Tag                | Trigger                                    |
|--------------------|--------------------------------------------|
| Click              | When selecting the announcer               |
| StartWork          | At the start of the workday (audio only)   |
| HalfOverWork       | When half of energy target is collected    |
| OverWork           | When energy target is fully collected      |
| AgentDie           | When an Agent dies                         |
| AgentPanic         | When an Agent panics                       |
| OnAgentPanicReturn | When an Agent recovers from panic          |
| AllDie             | When all Agents are dead                   |
| OnGetEGOgift       | When an Agent obtains an E.G.O Gift        |
| CounterToZero      | When an Abnormality escapes                |
| Suppress           | When an Abnormality is suppressed          |
| QliphothMeltdown   | When Qliphoth Meltdown level increases     |
| Rabbit             | When dispatching Rabbit Team               |
| RabbitReturn       | When Rabbit Team returns                   |
| Idle               | When no announcements for 65-90 seconds    |
| OnOverWork         | When clicking End Management (audio only)  |

=== Placeholders ===

You can use placeholders in your announcement text:

- #0 : Agent name (for AgentDie, AgentPanic, OnAgentPanicReturn, OnGetEGOgift)
- $0 : Abnormality name (for CounterToZero, Suppress)

=== Assigning Images ===

- Announcer.png : Default portrait image (512x512 pixels required)
- UI.png        : Selection button icon (345x213 pixels recommended)
- Tag images    : Portrait for specific announcements (512x512 pixels)

If an image doesn't match the required size, you'll be prompted to:
- Yes (Stretch)  : Distort to fit exact dimensions
- No (Crop)      : Scale while maintaining aspect ratio, crop excess
- Cancel         : Use original without resizing

=== Assigning Audio ===

- Click "Assign Sound..." to assign a WAV file to a tag
- You'll be prompted to normalize the audio volume
- Click the play button to preview the assigned audio

=== Random Announcements ===

1. Check "Random" checkbox
2. Set "Quantity" (max variants per tag, 1-10)
3. If Auto-Generate is enabled, numbered variants are created automatically
   (e.g., AgentDie_1, AgentDie_2, AgentDie_3)

=== Auto-Generate Tags ===

- When enabled, tags are automatically generated when you add a language
- Tags are regenerated when Random/Quantity settings change
- Disable to manually control which tags exist

=== Generate All Button ===

- Click "Generate All" to create all 16 base tags for the current language
- Useful when Auto-Generate is disabled or tags are missing
- Existing text content is preserved

=== Multi-Language Support ===

- Click "Add" to add a new language code
- Click "Delete" to remove a language and its text data
- Each language has its own set of tag texts
- Images and audio are shared across all languages

=== Border Color ===

- Click "Change Border Color" to customize the announcement frame color
- Adjust "Alpha" (0-255) for transparency

=== Loading Existing MOD ===

Click "Load Existing" and select the AnnouncersXML_LEB.xml file from an
existing mod to edit it.

=== Undo/Redo ===

- Click "Undo" to revert the last change
- Click "Redo" to restore an undone change
- Only one step of undo/redo is supported

--------------------------------------------------------------------------------
                        OUTPUT STRUCTURE
--------------------------------------------------------------------------------

YourMod/
  AnnouncersXML_LEB.xml
  AnnouncersImage_LEB/
    [AnnouncerName]/
      Announcer.png
      UI.png
      Announcer[TagName].png
  AnnouncersTEXT_LEB/
    [AnnouncerName]/
      [language]/
        [language].xml
  AnnouncersSounds_LEB/
    [AnnouncerName]/
      [TagName].wav

--------------------------------------------------------------------------------
                      ADDING TOOL LANGUAGES
--------------------------------------------------------------------------------

Place JSON files in the "Languages" folder to add new UI languages.
See en.json or ja.json as templates.

The file name (without extension) becomes the language code.
Include a "LanguageName" key for the display name in the dropdown.

--------------------------------------------------------------------------------
                           LICENSE
--------------------------------------------------------------------------------

This tool is provided as-is for creating Lobotomy Corporation mods.

--------------------------------------------------------------------------------
                           CREDITS
--------------------------------------------------------------------------------

Created with Claude Code

================================================================================
