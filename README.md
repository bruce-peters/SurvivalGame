# SurvivalGame
files for a survival 2d game Im working on

A top-down 2D survival game built in Unity with C#. The player survives in a forest by collecting
resources. It has a day-night cycle, crafting, and a procedurally generated world that can be saved and
loaded.

**Play it on itch.io:** https://bobcat9.itch.io/survival-2d

## Run it in the Unity editor

Prereqs:
- **Unity 2022.3.11f1** (from `ProjectSettings/ProjectVersion.txt`). Install it through Unity Hub. Any
  2022.3 LTS release should also open the project; Hub will offer to upgrade it.
- Packages (Unity's new Input System, URP 14, Cinemachine, 2D feature set, TextMeshPro) are listed in
  `Packages/manifest.json`. Unity downloads them on first open.

Steps:
1. `git clone https://github.com/bruce-peters/SurvivalGame.git`
2. In Unity Hub: **Add > Add project from disk** and pick the cloned folder. The first import takes a
   few minutes while Unity builds the `Library/` folder.
3. Open `Assets/Scenes/MainMenuScene.unity` and press **Play**. Start from the main menu. If you press
   Play in `GameScene` directly, no world gets loaded or created.
4. Press the main menu's Play button, then **New World**, enter a name and seed, and **Create World**.
   Saved worlds show up on the world-select screen.

To make a standalone build: **File > Build Settings** already lists the three scenes in order
(`MainMenuScene`, `WorldSelectScene`, `GameScene`). Pick a platform and press **Build**.

## Controls

Read from `Assets/Scripts/Player/PlayerControls.inputactions` and the scripts:

| Action | Keys |
|---|---|
| Move | WASD or arrow keys |
| Place block / use a chest or campfire | Left mouse button or J |
| Mine / break the highlighted block (hold) | Right mouse button or K |
| Open inventory and crafting | E |
| Drop held item | Q |
| Use inventory slot 1 to 9 (same as clicking it: picks up or swaps the held item) | 1 to 9 |
| Pause menu (Save & Quit) | Esc, M or Tab |
| Save world / reload world | Ctrl+E / Ctrl+R |

## Project structure

```
Assets/Scenes/                    MainMenuScene, WorldSelectScene, GameScene
Assets/Scripts/Player/            movement and the Input System action asset
Assets/Scripts/ProceduralGeneration/  noise-based map and biome generation
Assets/Scripts/Commands/          break, smelt, create-world and load-world commands
Assets/Scripts/Crafting/          recipes and crafting UI
Assets/Scripts/Items/             inventories (player, chest, campfire)
Assets/Scripts/WorldManager.cs    saving and loading worlds
Assets/TimeManager.cs             day-night cycle
Assets/LeanTween/                 third-party tweening library
```

Worlds are saved to `Application.persistentDataPath/saves`. On Windows that is
`%USERPROFILE%\AppData\LocalLow\ClimbingBobcat\SurvivalGame\saves`.
