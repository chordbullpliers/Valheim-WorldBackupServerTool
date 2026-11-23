<p align="center">
  <img src="https://i.postimg.cc/cCPGZZnd/banner.png" alt="Valheim World Vault — Rolling World/Character Backups & 1-Click BepInEx Mod Toggle" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Valheim%20World%20%26%20Mod%20Vault-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-valheim--vault--v1.2-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Valheim World Vault — Rolling World/Character Backups & 1-Click BepInEx Mod Toggle

**Had a Valheim world reset to Day 1 after a Steam Cloud sync conflict, or need to disable BepInEx mods in one click before joining a vanilla friend's server? Archive worlds_local & characters_local into rolling ZIPs and switch Modded ↔ Vanilla cleanly.**

Valheim World Vault protects IronGate save files in `%USERPROFILE%\AppData\LocalLow\IronGate\Valheim` on Windows: **backing up `.fwl`/`.db` worlds and `.fch` Vikings outside Steam Cloud's overwrite reach, and toggling `winhttp.dll` / `BepInEx` cleanly for vanilla multiplayer**.

This project is aimed at **Valheim on Windows 10/11 PC (Steam)** for safeguarding multi-hundred-hour builds and switching between modded solo worlds and vanilla co-op servers.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Valheim world spawns empty terrain with all buildings wiped ('Day 1 bug') | Steam Cloud or corrupted `.db` file causes Valheim to regenerate fresh seed | Restore matching `.fwl` + `.db` pair from `ValheimWorldVault` snapshots |
| Cannot join a vanilla friend's Valheim server while BepInEx is installed | Active `winhttp.dll` / `BepInEx` hooks fail server version/mod checks | Click **Switch to Vanilla Mode** (stashes `winhttp.dll` cleanly in 1 click) |
| Moving a local co-op world onto a Valheim Dedicated Server | World files split between `worlds_local` and Steam Cloud `userdata` | Export unified `.fwl` + `.db` world bundle ready for dedicated server `worlds_local` |
| In-game `.old` backup gets overwritten after two quick relogs | Valheim keeps only a limited rotation of `.db.old` files | Keep 30 external `.zip` snapshots in `Documents\Valheim-WorldVault` |

## Download for Windows

[**Download ValheimWorldVault.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/ValheimWorldVault.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `ValheimWorldVault.exe`? (Key features)

- Scans `%USERPROFILE%\AppData\LocalLow\IronGate\Valheim\worlds_local` and `characters_local` (plus Steam Cloud `892970\remote`).
- Creates timestamped `.zip` backups of matching `.fwl` + `.db` world pairs and `.fch` character files.
- One-click **BepInEx Vanilla Toggle** disables/re-enables `winhttp.dll` without deleting your `BepInEx\plugins` or configs.
- Exports clean `.fwl` + `.db` world packages for dedicated servers.

### Sample Output

```text
[ValheimWorldVault] Scanned AppData\LocalLow\IronGate\Valheim
[OK]   Worlds Found     : Midgard_2026 (.fwl + .db: 42.6 MB) | Ashlands_Base (31.4 MB)
[OK]   Characters Found : Ragnar.fch (1.8 MB)
[OK]   Snapshot Saved   : Documents\Valheim-WorldVault\Midgard_2026_2026-11-23.zip
[INFO] BepInEx Status   : ENABLED (14 plugins in BepInEx\plugins)
```

The release ZIP is named `ValheimWorldVault.zip`; the Windows executable inside is named `ValheimWorldVault.exe`.

1. Close Valheim World Vault before updating or replacing executable files.
2. Click **Download ValheimWorldVault.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `ValheimWorldVault.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit) with Valheim installed.

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `ValheimWorldVault.exe` runs locally without uploading your personal files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Preventing the notorious Valheim 'Day 1 empty world' wipe

Keeps independent `.zip` copies of `.fwl` + `.db` pairs outside Steam Cloud's sync folder.

### Seamless switching between Modded and Vanilla servers

Toggling `winhttp.dll` lets you join vanilla servers in seconds without rebuilding your BepInEx setup.

### Easy dedicated server world migration

Bundles both `.fwl` metadata and `.db` terrain/building data together so neither half is forgotten.

### Automatic pre-restore safety snapshot

Backs up current files before restoring any older world archive.

## Default folders and configuration paths

Valheim stores local worlds and characters in `%USERPROFILE%\AppData\LocalLow\IronGate\Valheim`:

```text
%USERPROFILE%\AppData\LocalLow\IronGate\Valheim\
```

Typical directory layout:

```text
%USERPROFILE%\AppData\LocalLow\IronGate\Valheim\
├── worlds_local\
│   ├── Midgard.fwl
│   └── Midgard.db
└── characters_local\
    └── Viking.fch
```

Always close Valheim completely before restoring world files or toggling BepInEx.

## Quick start guide

Follow these steps to get started:

1. **Close Valheim completely.** Extract `ValheimWorldVault.zip` and launch `ValheimWorldVault.exe`.
2. **Click **Back Up All Worlds & Characters** to save a dated `.zip` snapshot.** Verify both `.fwl` and `.db` files appear in the world list.
3. **Use **Toggle Vanilla / Modded** whenever switching between modded solo play and vanilla servers.** Restore any snapshot in 1 click if a world ever glitches.

### Data safety note

Valheim World Vault archives existing `.fwl`/`.db`/`.fch` files before applying any restore.

## What the status summary shows

Valheim World Vault displays **detected worlds, `.db` file sizes, character `.fch` files, BepInEx active status, and backup archive path**.

## FAQ

**Why do I need both the .fwl and .db files for a Valheim world?**

The `.fwl` file stores the world seed and metadata, while the `.db` file stores all terrain edits, chests, and player-built structures—both must match.

**How does the 1-click BepInEx Vanilla Toggle work?**

It renames `winhttp.dll` in your Valheim folder to `winhttp.dll.disabled` so BepInEx does not load, while keeping all your plugins and config files intact.

**Does it work with Valheim Dedicated Servers?**

Yes—you can export any local world as a ready-to-upload `.fwl` + `.db` server pair.

## Useful reading

- [Valheim on Steam](https://store.steampowered.com/app/892970/Valheim/)

## More Windows Gaming Utilities

- [CoopHost-GameServerManager](../CoopHost-GameServerManager) — 1-click dedicated server manager for Minecraft, Palworld & Valheim
- [Palworld-WorldSaveFixer](../Palworld-WorldSaveFixer) — Palworld Level.sav backup vault & Co-op to Server migrator
- [ModDrop-UniversalPakInstaller](../ModDrop-UniversalPakInstaller) — Drag-and-drop ZIP/PAK mod installer with conflict check
- [QuickSave-HotkeySnapshotVault](../QuickSave-HotkeySnapshotVault) — F5/F9 hotkey save snapshot & restore vault for any PC game

*Independent community project. Not affiliated with Iron Gate AB, Coffee Stain Publishing, Valve, or Steam.*
