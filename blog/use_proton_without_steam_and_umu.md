# 直接使用 steam_runtime 与 proton-ge 运行游戏
以下是最小必要变量使用示例：
```bash
PROTON_USE_WAYLAND=1 UMU_ID=0 STEAM_COMPAT_CLIENT_INSTALL_PATH= STEAM_COMPAT_DATA_PATH=~/Games/test /home/Fia/.local/share/Steam/steamapps/common/SteamLinuxRuntime_4/_v2-entry-point /home/Fia/.local/share/Steam/compatibilitytools.d/GE-Proton11-1/proton waitforexitandrun /home/Fia/Games/StellaSora/drive_c/YostarGames/StellaSora_CN/xtlr.exe
```
`PROTON_USE_WAYLAND=1` proton-ge 选项，启用 wayland<br>
`UMU_ID=0` proton-ge 选项，用于 protonfixs<br>
`STEAM_COMPAT_CLIENT_INSTALL_PATH=` proton 选项，steam 安装位置<br>
`STEAM_COMPAT_DATA_PATH=~/Games/test` proton 选项，wine 前缀目录<br>

**NOTE**: proton 使用绝对路径运行，否则可能出现意外行为（wayland 无法使用）