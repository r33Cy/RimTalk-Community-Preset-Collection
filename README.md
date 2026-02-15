# RimTalk Community Preset Collection

A community-driven repository of custom presets for the **RimTalk** mod.

### Prerequisites

* [RimTalk (Steam Workshop)](https://steamcommunity.com/sharedfiles/filedetails/?id=3551203752)

---

## How to use

1. **Download** any `preset.json` file from this collection.
2. **Copy** the downloaded file to the specific directory for your OS:

### **Windows**
`C:\Users\%USERNAME%\AppData\LocalLow\Ludeon Studios\RimWorld by Ludeon Studios\Config\RimTalk\Presets`

### **macOS**
`~/Library/Application Support/RimWorld by Ludeon Studios/Config/RimTalk/Presets`

### **Linux (Native)**
`~/.config/unity3d/Ludeon Studios/RimWorld by Ludeon Studios/Config/RimTalk/Presets`

### **Steam Deck (SteamOS/Proton)**
`~/.local/share/Steam/steamapps/compatdata/294100/pfx/drive_c/users/steamuser/AppData/LocalLow/Ludeon Studios/RimWorld by Ludeon Studios/Config/RimTalk/Presets`

> [!TIP]
> On Linux and Steam Deck, folders starting with a dot (like `.local`) are hidden. Press `Ctrl + H` in your file manager to reveal them.

3. **Launch** RimWorld.
4. **Open** RimTalk's mod settings.
5. **Switch to Advanced Mode** (if not already enabled).
6. **Go to the Prompt Setting**, select **Import**, and load your chosen preset.
7. **Activate** the loaded preset.

---

## How to contribute

We love new presets! To add yours to the collection:

1. **Fork/Check out** this repository.
2. **Create a folder** under `/presets/` named after your username or alias.
3. **Add your exported JSON** file to that folder.
4. **Add a plain text file of your preset** file to that folder, so others can read the ruleset easily.
4. **Include a README.md** in your folder using the template provided in `/templates/CONTRIBUTOR_README.md`.
5. **Create a Pull Request** with a brief description of what your preset does.

### Directory Structure Example

```
presets/
├── your-username/
│   ├── cool-preset.json
    ├── cool-preset.txt
│   └── README.md
```