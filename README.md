
# HelloMario

**Super Mario 64's Mario in Hello Neighbor.** SM64's own code (through [libsm64](https://github.com/libsm64/libsm64))
runs his physics, moves, animations, model and sounds, while he runs through the Neighbor's house. The Neighbor can
still catch him, and doors, ladders, items and cutscenes keep working.

<img width="1280" height="720" alt="phOGAqdt-7U-HD" src="https://github.com/user-attachments/assets/69c5e3cc-ce67-4955-baa2-f497a772954c" />

> Unofficial fan project, not affiliated with Nintendo, tinyBuild or Dynamic Pixels. The download contains **no ROM
> and no Nintendo assets**: you give the installer **your own Super Mario 64 (USA) ROM**, and Mario's model, textures,
> animations and sounds are read from it on your PC. Please don't ask for or share ROMs in the issues.

## Features

- **Real SM64 Mario**: running, jumping (double, triple, long, wall kick), punches and kicks, crouch, ground pound, SM64's voice and
  sound effects.
- **He can interact**: doors, ladders, windows (punch or kick them), picking up and throwing items, being caught
  by the Neighbor, and Mario replaces Nicky in the cutscenes.
- **Extras**: lit Bob-ombs to carry and throw (F3), metal cap (F4), wing cap and flight (F5).

## Requirements

- **Hello Neighbor** (full game) on Steam, on Windows
- **A Super Mario 64 ROM of your own**: the **US** version, dumped from your own cartridge (`.z64`, `.v64` or `.n64`,
  8 MB). The installer checks it (SHA-1 `9bef1128717f958171a4afac3ed78ee2bb4e86ce`). Other versions and ROM hacks don't work.

## Install

1. Download `HelloMario-1.0.0.zip` from [Releases](../../releases) and unzip it anywhere.
2. Copy your ROM into the empty **`rom`** folder next to `Install.bat`.
3. Close Hello Neighbor, then double-click **`Install.bat`**. It finds Hello Neighbor through Steam, checks the ROM in the `rom`
   folder (if there is none it says so and stops, nothing is installed), and installs the mod with
   [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS).
   - Windows may warn about running a script from the internet. Choose "More info", then "Run anyway".
4. Start Hello Neighbor from Steam as usual and load a level. Mario stands in front of you.

## Controls

| Key | |
|---|---|
| WASD / pad stick | run |
| Space / A | jump |
| Left mouse / X | punch / kick |
| Left Ctrl | crouch (ground pound in the air, long jump when running) |
| Mouse / right stick | camera |
| E | doors, ladders, pick up (as in the game) |
| Right mouse | drop / throw what Mario carries |
| F3 / F4 / F5 | Bob-omb / metal cap / wing cap |
| F6 | Mario in cutscenes on / off |
| F7 | Mario in front of you again (if he gets stuck) |
| F8 | the mod on / off |
| F9 | read the level's collision again |

## Uninstall

Double-click **`Uninstall.bat`**. It removes everything the installer added to Hello Neighbor, including UE4SS if the
installer put it there (a UE4SS you had before stays, and any file the installer replaced is put back), and the copy of
the ROM it made. Your original ROM file is never touched.

## What it changes

Only Hello Neighbor's folder: UE4SS (`dwmapi.dll` and the `ue4ss` folder in `HelloNeighbor\Binaries\Win64`) and the
mod's two UE4SS mods (`HnMario`, `HnMarioNative`). The installer copies your ROM into `HnMarioNative\dlls` as
`baserom.us.z64`, so the mod keeps working if you move the original. Replaced files are kept as `*.before-hellomario`,
and `installed.txt` lists everything that was added.

## Troubleshooting

- **"not the Super Mario 64 (USA) ROM"**: see Requirements. A patched or trimmed ROM fails the check.
- **Mario doesn't appear**: press F7, then F8 twice.
- **Antivirus / SmartScreen warnings**: UE4SS loads as a `dwmapi.dll` next to the game, and the mod is a DLL that draws
  into the game's frame. Check that your download matches the SHA-256 on the release page
  (PowerShell: `Get-FileHash HelloMario-1.0.0.zip`).

Single-player only. Other Hello Neighbor mods installed the same way (HelloSonic, HelloPortal ...) were not made to run
together with this one.

## Source

`sm64.dll` is libsm64 with small changes of ours (carrying items, going through doors, cutscene poses). The changes are
`libsm64-hellomario.patch` on the release page, against libsm64 commit `fd11813`. The installer scripts are plain
PowerShell in `scripts\`.

## Credits

- **Super Mario 64** and Mario: Nintendo. Their content is read from your own ROM.
- **Hello Neighbor**: tinyBuild / Dynamic Pixels.
- **[libsm64](https://github.com/libsm64/libsm64)** (CC0) and the SM64 decompilation project: Mario's code as a library.
- **[UE4SS](https://github.com/UE4SS-RE/RE-UE4SS)** (MIT): the scripting system the mod runs on.
- **[MinHook](https://github.com/TsudaKageyu/minhook)** (BSD-2-Clause).
- Made with the help of AI coding tools.

Licence: MIT (see `LICENSE`) for the mod's own code. The game content it reads stays Nintendo's and tinyBuild's.
