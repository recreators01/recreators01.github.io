# 直接使用 steam_runtime 与 proton-ge 运行游戏
以下是最小必要变量使用示例：
```bash
PROTON_USE_WAYLAND=1 SteamGameId=0 STEAM_COMPAT_CLIENT_INSTALL_PATH= STEAM_COMPAT_DATA_PATH=~/Games/test /home/Fia/.local/share/Steam/steamapps/common/SteamLinuxRuntime_4/_v2-entry-point /home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton11-1/proton waitforexitandrun /home/Fia/Games/StellaSora/drive_c/YostarGames/StellaSora_CN/xtlr.exe
```
`PROTON_USE_WAYLAND=1` proton-ge 选项，启用 wayland<br>
`SteamGameId=0` proton 选项，不设置可能会出现意外行为（比如视频无法播放）
`STEAM_COMPAT_CLIENT_INSTALL_PATH=` proton 选项，steam 安装位置<br>
`STEAM_COMPAT_DATA_PATH=~/Games/test` proton 选项，wine 前缀目录<br>

**NOTE**: proton 使用绝对路径运行，否则可能出现意外行为（wayland 无法使用）
**NOTE**: 设置 SteamGameId=0，否则可能出现意外行为（比如视频无法播放）

以下是使用 `umu` 运行时捕获的命令：
```bash
PROTON_USE_WAYLAND=1 WAYLANDDRV_PRIMARY_MONITOR=eDP-1 WINEPREFIX=/home/Fia/Games/stella_soral GAMEID=0 PROTON_CRASH_REPORT_DIR=/tmp/umu_crashreports PROTONPATH=/home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton10-34 STEAM_COMPAT_APP_ID=33570c26939775d83ee2057a63cfc13d STEAM_COMPAT_TOOL_PATHS=/home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton10-34:/home/Fia/.local/share/umu/steamrt3 STEAM_COMPAT_LIBRARY_PATHS=/home STEAM_COMPAT_MOUNTS=/home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton10-34:/home/Fia/.local/share/umu/steamrt3 STEAM_COMPAT_INSTALL_PATH=/home/Fia/Games/stella_soral/drive_c/YostarGames/StellaSora_CN STEAM_COMPAT_CLIENT_INSTALL_PATH= STEAM_COMPAT_DATA_PATH=/home/Fia/Games/stella_soral STEAM_COMPAT_SHADER_PATH=/home/Fia/Games/stella_soral/shadercache STEAM_COMPAT_LAUNCHER_SERVICE= FONTCONFIG_PATH= EXE=/home/Fia/Games/stella_soral/drive_c/YostarGames/StellaSora_CN/xtlr.exe SteamAppId=0 SteamGameId=0 STEAM_RUNTIME_LIBRARY_PATH=/usr/lib:/home/Fia/Games/stella_soral/drive_c/YostarGames/StellaSora_CN:/usr/lib32 STORE= PROTON_VERB=waitforexitandrun UMU_ID=0 UMU_ZENITY= UMU_NO_RUNTIME= UMU_RUNTIME_UPDATE= UMU_NO_PROTON= UMU_CONTAINER_NSENTER= RUNTIMEPATH=/home/Fia/.local/share/umu/steamrt3 UMU_STEAM_GAME_ID= UMU_INVOCATION_ID=8fb1930ce045e154c76af2c4e73cd991 /home/Fia/.local/share/umu/steamrt3/umu --verb=waitforexitandrun -- /home/Fia/.local/share/umu/umu-shim /home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton10-34/proton waitforexitandrun /home/Fia/Games/stella_soral/drive_c/YostarGames/StellaSora_CN/xtlr.exe
```
`PROTON_USE_WAYLAND=1` proton-ge 选项，启用 wayland<br>
`UMU_ID=0` proton-ge 选项，用于 protonfixs<br>
`STEAM_COMPAT_CLIENT_INSTALL_PATH=` proton 选项，steam 安装位置<br>
`STEAM_COMPAT_DATA_PATH=~/Games/test` proton 选项，wine 前缀目录<br>
