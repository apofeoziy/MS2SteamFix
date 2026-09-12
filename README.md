# MS2SteamFix

MS2SteamFix is a launch wrapper for Marathon intended to help alleviate frame pacing and stuttering issues for Steam users. Before starting Marathon, it temporarily denies execute access to Steam's overlay renderer DLLs, then restores the original permissions after exiting the game.

Please note that blocking the Steam Overlay DLLs can also affect overlay-dependent features such as Steam Input, notifications, Game Recording, and Remote Play. This program temporarily changes only the ACL metadata of the overlay DLLs; it does not alter their contents. It does not inject code, inspect process memory, modify game files, change Steam configuration, or bypass BattlEye.

## Installation

Download [steamfix.exe](https://github.com/apofeoziy/MS2SteamFix/releases/latest/download/steamfix.exe) and place it directly in your game's directory.

Then, open Marathon's launch options in Steam:

1. In Steam right-click **Marathon** in your library and select **Properties**.
2. Find the **Launch Options** field under the **General** tab and paste the command below.

```text
"C:\path\to\Marathon\steamfix.exe" %command%
```

Replace `C:\path\to\Marathon` with the actual location of your Marathon installation. The example path below is for a default Steam installation; if your game is on another drive, use that drive letter and the complete path instead:

```text
"C:\Program Files (x86)\Steam\steamapps\common\Marathon\steamfix.exe" %command%
```

## Building from Source

### Prerequisites

Building MS2SteamFix requires Windows and the Microsoft Visual C++ toolchain.

Install either Visual Studio or Visual Studio Build Tools with the Desktop development with C++ workload selected. Make sure to include the MSVC compiler and a Windows SDK. Run the following commands from a Visual Studio Developer command prompt:

```batch
make.cmd configure
```

```batch
make.cmd build
```

## Windows Defender

The published binary may be flagged as a false positive by Windows Defender. This is a known issue.

If your Windows Defender reports a detection, [please follow these instructions to clear cached detections and update malware definitions.](docs/WINDOWS_DEFENDER.md)
