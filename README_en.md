# Announcer Creator Tool

A GUI tool for creating Announcer MODs for Lobotomy Corporation.

## Features

- Create and manage multiple announcers
- Edit announcement text for 16 trigger scenarios
- Multi-language support for announcement text (jp, en, etc.)
- Assign portrait images for each announcement
- Assign voice audio (WAV) for each announcement
- Audio normalization feature
- Audio preview playback
- Image resizing (scale/crop) for incorrect sizes
- Random announcement variants support
- Portrait variation (Expression) support
- Border color customization with alpha transparency

## Requirements

- Windows 10/11 (64-bit)
- .NET 8.0 Runtime (included in self-contained build)

## Installation

1. Extract the zip file to any folder
2. Ensure the `Languages` folder is in the same directory as the exe
3. Run `AnnouncerTool.exe`

## How to Use

### Creating a New Announcer

1. Launch the tool
2. Enter the announcer name in the text field (English characters recommended)
3. Select a language for the announcement text (default: jp)
4. Click on each tag in the list and enter the announcement text
5. Assign images:
   - **Announcer.png**: Default portrait (512x512 required)
   - **UI.png**: Selection button icon (345x213 recommended)
   - **Tag images**: Portrait for specific announcements
6. (Optional) Assign WAV audio files for voice lines
7. Select a save folder and click "Save Mod"

### Tag Descriptions

| Tag | Trigger |
|-----|---------|
| Click | When selecting the announcer |
| StartWork | At the start of the workday (audio only) |
| HalfOverWork | When half of energy target is collected |
| OverWork | When energy target is fully collected |
| AgentDie | When an Agent dies |
| AgentPanic | When an Agent panics |
| OnAgentPanicReturn | When an Agent recovers from panic |
| AllDie | When all Agents are dead |
| OnGetEGOgift | When an Agent obtains an E.G.O Gift |
| CounterToZero | When an Abnormality escapes |
| Suppress | When an Abnormality is suppressed |
| QliphothMeltdown | When Qliphoth Meltdown level increases |
| Rabbit | When dispatching Rabbit Team |
| RabbitReturn | When Rabbit Team returns |
| Idle | When no announcements for 65-90 seconds |
| OnOverWork | When clicking End Management button (audio only) |

### Placeholders

- `#0` - Agent name (for AgentDie, AgentPanic, OnAgentPanicReturn, OnGetEGOgift)
- `$0` - Abnormality name (for CounterToZero, Suppress)

### Random Announcements

1. Check "Random" checkbox
2. Set "Quantity" (max variants per tag, 1-10)
3. Use "Add" button to create numbered variants (e.g., AgentDie_1, AgentDie_2)

### Loading Existing MOD

Click "Load Existing" and select the `AnnouncersXML_LEB.xml` file from an existing mod.

## Output Structure

```
YourMod/
├── AnnouncersXML_LEB.xml
├── AnnouncersImage_LEB/
│   └── [AnnouncerName]/
│       ├── Announcer.png
│       ├── UI.png
│       └── Announcer[TagName].png
├── AnnouncersTEXT_LEB/
│   └── [AnnouncerName]/
│       └── [language]/
│           └── [language].xml
└── AnnouncersSounds_LEB/
    └── [AnnouncerName]/
        └── [TagName].wav
```

## Adding Tool Languages

Place JSON files in the `Languages` folder to add new UI languages.
See `en.json` or `ja.json` as templates.

## License

This tool is provided as-is for creating Lobotomy Corporation mods.

## Credits

Created with Claude Code
