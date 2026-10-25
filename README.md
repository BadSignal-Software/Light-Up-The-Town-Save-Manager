# Light Up The Town - Save Manager

[![Game Version](https://img.shields.io/badge/Game_Version-1.1.1-blue)](https://github.com/BadSignal-Software)
[![UE4SS](https://img.shields.io/badge/UE4SS-v3.0.1-orange)](https://github.com/UE4SS-RE/RE-UE4SS)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A UE4SS mod for **Light Up The Town** that seamlessly integrates a **three-slot save system** into the main menu. Choose your save slot when clicking **New Game** or **Continue**, fully styled to match the game's native UI.

> [!NOTE]  
> Unofficial fan-made mod. Not affiliated with or endorsed by the game's developer. Also sometimes when clicking "new game" the real button function returns and says "are you sure you want to overwrite?" make sure to press "no" then click the button again. We are working to fix this, but as we cannot reproduce the problem reliably it is harder to fix. If you have had this issue, please send us the logs in an issue thread so we can fix it.

> [!WARNING]  
> **BACK UP YOUR SAVES!** While this mod includes safety backups, we take no responsibility for potential save data loss. Use at your own risk.

---

## ✨ Features

- **3 Dedicated Save Slots:** 
  - **Slot 1:** Automatically takes your existing save file upon installation.
  - **Slots 2 & 3:** Start empty for new, side-by-side playthroughs.
- **Interactive Main Menu Slot Picker:** Select your slot directly from **New Game** or **Continue**.
- **Overwrite Protection:** Prompts a **Yes/No** confirmation before wiping an existing save slot on a fresh game run.
- **At-a-Glance Metadata:** View your **last saved level name** and **total playtime** for each individual slot.
- **Smart Auto-Saving:** Guarantees your progress is synchronized to the correct slot whenever you save, quit, or return to the main menu.
- **Native Aesthetic:** Built using the game's original fonts, color palette, and rounded button styles.
- **Automatic First-Run Backup:** Automatically preserves your original pre-mod save files inside an untouched `original_backup` folder.
- **Mod Manager Compatible:** Includes `modmanager.json` for full integration with the Light Up The Town Mod Manager.
- **‼️ The mod manager is a dependency ‼️** You can get it at https://github.com/BadSignal-Software/Light-Up-The-Town-Mod-Manager
- mod manager.json is included so the mod will be setup ready for modmanager installation.

---

## 🛠️ Compatibility

Tested and built for **Game Version 1.1.1** with **UE4SS 3.0.1**.

Fully compatible alongside:
- 🛠️ [Light Up The Town - In-Game Mod Manager](https://github.com/BadSignal-Software/Light-Up-The-Town-Mod-Manager)
- 🌐 [Light Up The Town - Multiplayer Mod (Lutt-Net)](https://github.com/BadSignal-Software/Light-Up-The-Town-Multiplayer-Mod)

---

## 📥 Installation

> [!IMPORTANT]  
> Ensure **UE4SS** is installed first, including placing `dwmapi.dll` in `LightUpTheTown\Binaries\Win64\`.

1. **Manual Save Backup:** Before installing, create a copy of your save folder somewhere safe:
   ```text
   %LOCALAPPDATA%\LightUpTheTown\Saved\SaveGames

```

2. **Navigate to Mods Directory:** Go to:
```text
LightUpTheTown\Binaries\Win64\ue4ss\Mods\

```


3. **Create Mod Folder:** Create a folder named `LUTTSaveManager`.
4. **Copy Mod Files:** Structure the contents as follows:
```text
LUTTSaveManager/
├── enabled.txt          (empty file)
├── modmanager.json
└── Scripts/
    ├── main.lua
    └── sm_ui.lua

```


5. **Launch:** Start the game. **New Game** and **Continue** will now launch the slot selection screen.

---

## ⚙️ How It Works

Because the native game engine only tracks a single save directory, **Save Manager** operates as a dynamic switcher, maintaining segregated copies per slot:

| Item | Location |
| --- | --- |
| **Live Save Directory** | `%LOCALAPPDATA%\LightUpTheTown\Saved\SaveGames` |
| **Slot Storage (1, 2, 3)** | `...\SaveGames\LUTTSlots\slot1`, `slot2`, `slot3` |
| **First-Run Backup** | `...\SaveGames\LUTTSlots\original_backup` |
| **Slot Metadata** | `...\SaveGames\LUTTSlots\slots.txt` |

*When selecting a slot, the mod writes current progress to the active slot folder, clears the live directory, mounts the newly selected slot's files, and signals the engine to refresh context.*

---

## 💡 Good to Know

* **Playtime Tracking:** Playtime tracking begins *after* mod installation. Pre-existing saves start at 0h 0m.
* **Level Info:** Displayed level names reflect the last location where the game performed an autosave/manual save.
* **Native Prompt Override:** If the game's built-in *"Overwrite progress?"* prompt appears when launching a New Game, select **NO** and let the mod UI handle the confirmation screen instead.

---

## 🗑️ Uninstalling

1. Launch the game, press **Continue**, and select **Slot 1** to ensure your primary save is active in the live save folder.
2. Exit the game.
3. Delete the `LUTTSaveManager` directory from `...\ue4ss\Mods\`.

*(Optional) Additional save slots will remain safely archived under `SaveGames\LUTTSlots\` if you wish to backup or reuse them later.*

---

## 🔍 Troubleshooting

Logs are generated directly to help diagnose potential issues:

```text
LightUpTheTown\Binaries\Win64\ue4ss\Mods\LUTTSaveManager\savemanager_log.txt

```

If you encounter bugs, please attach `savemanager_log.txt` along with your primary `UE4SS.log` when submitting an issue.

---

## 👤 Credits

Developed and maintained by **ShadowCanvas815**.
