# Light Up The Town - Save Manager

A UE4SS mod for **Light Up The Town** that adds **three save slots** to the main menu. Pick a slot when you press **New Game** or **Continue**, in the same art style as the game's own menus.

> Unofficial fan-made mod. Not affiliated with the game's developer.

## What it does

- **Three save slots.** Slot 1 is your existing save from before the mod was installed. Slots 2 and 3 start empty, so you can run separate playthroughs side by side.
- **New Game opens a slot picker.** Choose the slot to start a fresh game in.
- **Overwrite protection.** Starting a new game on a slot that already has a save asks **yes** or **no** before anything is wiped.
- **Continue asks which slot to load.** Only slots that contain a save can be picked.
- **Slot info at a glance.** Each slot shows the **level you last saved in** and **how long you have played** on it.
- **Save and Quit goes to the right slot.** Saving, then quitting or returning to the menu, always writes to the slot you are playing, never to the others.
- **Looks like the game.** The picker and the yes/no prompt use the game's font, colours and rounded buttons.
- **Automatic backup.** On first run your current save is copied to an untouched `original_backup` folder.
- **Shows up in the Mod Manager.** Includes a `modmanager.json` so it is listed with its description.

## Compatibility

Works alongside:

- [Light Up The Town - In-Game Mod Manager](https://github.com/BadSignal-Software/Light-Up-The-Town-Mod-Manager)
- [Light Up The Town - Multiplayer Mod (Lutt-Net)](https://github.com/BadSignal-Software/Light-Up-The-Town-Multiplayer-Mod)

Built and tested with UE4SS 3.0.1 and game version 1.1.1.

## Installation

1. Install **UE4SS** for the game (see the Mod Manager or Multiplayer Mod pages above for the `dwmapi.dll` setup).
2. **Back up your saves.** Copy this folder somewhere safe:
   `C:\Users\<you>\AppData\Local\LightUpTheTown\Saved\SaveGames`
3. In `LightUpTheTown\Binaries\Win64\ue4ss\Mods\`, create a folder called `LUTTSaveManager`.
4. Put these files in it:
   ```
   LUTTSaveManager\
     enabled.txt          (empty file)
     modmanager.json
     Scripts\
       main.lua
       sm_ui.lua
   ```
5. Start the game. On the main menu, **New Game** and **Continue** now open the slot picker.

## How it works

The game only knows about one set of save files. The mod keeps one copy of that set per slot and swaps them in and out when you pick a slot.

| What | Where |
| --- | --- |
| Live save (the slot you are playing) | `%LOCALAPPDATA%\LightUpTheTown\Saved\SaveGames` |
| Slot 1, 2, 3 | `...\SaveGames\LUTTSlots\slot1`, `slot2`, `slot3` |
| Untouched first-run backup | `...\SaveGames\LUTTSlots\original_backup` |
| Play time and level names | `...\SaveGames\LUTTSlots\slots.txt` |

When you pick a slot, the mod copies the slot you were on out of the live folder, loads the chosen slot's files in, and tells the game to reload them. Every time the game saves, and again when you return to the menu or quit, the live files are copied back into the active slot.

## Good to know

- **Play time only counts from when the mod is installed.** The game never recorded it, so older saves start at zero.
- **The level name is the last level you saved in.**
- **Back up your saves** before the first run. The mod also keeps `original_backup`, but a second copy costs nothing.
- Occasionally the game's own button can react before the mod does. If you ever see the game's "override progress?" prompt after pressing New Game, answer **No**.

## Uninstalling

1. On the main menu, press **Continue** and pick **slot 1** so your original save is the one in the live folder.
2. Quit the game and delete the `LUTTSaveManager` folder.

Your other slots stay in `SaveGames\LUTTSlots` if you want to keep them.

## Troubleshooting

The mod writes a log to `Mods\LUTTSaveManager\savemanager_log.txt`. If something goes wrong, include that file and the UE4SS log when you report it.

## Credits

Made by ShadowCanvas815.
