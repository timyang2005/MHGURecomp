<p align="center"><img src="docs/images/logo.webp" alt="GU Recomp" width="481"></p>

<p align="center"><a href="README.md">English</a> · <a href="README.es.md">Español</a> · <b>简体中文</b></p>

<p align="center">
  <a href="https://github.com/morerokk/MHGURecomp/releases/latest"><img src="https://img.shields.io/github/v/release/morerokk/MHGURecomp?style=flat-square&label=release&labelColor=1d1e22&color=c58a2e" alt="最新版本"></a>
  <a href="https://github.com/morerokk/MHGURecomp/releases"><img src="https://img.shields.io/github/downloads/morerokk/MHGURecomp/total?style=flat-square&label=downloads&labelColor=1d1e22&color=c58a2e" alt="全部版本下载量"></a>
  <a href="#requirements"><img src="https://img.shields.io/badge/platforms-Windows%20%C2%B7%20Linux%20%C2%B7%20Android-c58a2e?style=flat-square&labelColor=1d1e22" alt="支持平台：Windows、Linux 与 Android"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/morerokk/MHGURecomp?style=flat-square&labelColor=1d1e22&color=c58a2e" alt="许可证：MIT"></a>
  <a href="https://github.com/morerokk/MHGURecomp/stargazers"><img src="https://img.shields.io/github/stars/morerokk/MHGURecomp?style=flat-square&label=stars&labelColor=1d1e22&color=c58a2e" alt="GitHub 星标"></a>
</p>

<p align="center">
  <a href="https://discord.gg/mdNPWfKBXf"><img src="https://img.shields.io/badge/Discord-MHGU%20Mod%20Community-5865f2?style=flat-square&logo=discord&logoColor=white&labelColor=1d1e22" alt="加入 MHGU Mod 社区 Discord"></a>
  <a href="https://github.com/Oddity-git/MHGURecomp-mods"><img src="https://img.shields.io/badge/mods-tested%20mod%20list-2ea44f?style=flat-square&logo=github&labelColor=1d1e22" alt="已测试 Mod 列表"></a>
</p>

<p align="center">
  <a href="https://github.com/morerokk/MHGURecomp/releases/latest"><b>下载</b></a> ·
  <a href="#installation">安装</a> ·
  <a href="#android">Android</a> ·
  <a href="#controls">操作</a> ·
  <a href="#settings">设置</a> ·
  <a href="#mods">Mod</a> ·
  <a href="#building-from-source">从源码构建</a>
</p>

# MHGU Recomp

《怪物猎人 XX / Generations Ultimate》（Nintendo Switch 版，版本 1.4.0）的**原生 PC 移植**：把游戏的 32 位 ARM 代码静态重编译为 C，再放到宿主运行时上执行。Switch 的系统服务与 NVN 图形 API 在 Windows、Linux 和 Android 上被重新实现，渲染使用 Vulkan。

> **不包含任何游戏文件。** 你需要自己拥有一份游戏，并从自己的 Switch 中提取。本项目不提供提取方法，也不提供游戏文件、密钥或相关链接。

**当前状态：完全可玩**，单人与联机均可。仍可能存在零星 bug，遇到问题时请附上 `log.txt` [提交 issue](https://github.com/morerokk/MHGURecomp/issues/new/choose)。

<a id="what-it-adds"></a>
## 相比 Switch 原版新增了什么

| 方面 | 你会得到 |
| --- | --- |
| **画面** | 分辨率、渲染分辨率（超采样）、MSAA、FXAA、FSR 3.1 超分、HDR 输出、垂直同步、更远的绘制距离 |
| **屏幕** | 任意宽屏比例（16:10、16:9 或更宽），超宽屏提供 HUD 位置调整选项 |
| **帧率** | 30–240 fps 之间任意帧率，并修复了 GU 在模拟器上高帧率时常见的 bug |
| **操作** | 几乎支持任意手柄（SDL），也支持键盘 + 鼠标 |
| **联机** | 通过「本地无线通信」在线游玩。内置在线服务器，也可自建服务器，或转发 39500 端口与好友直连 |
| **联机选项** | 小怪物在玩家间同步、怪物血量可按人数缩放、村庄任务可在集会所游玩、紧急任务全员共享完成记录 |
| **便利性** | 按 A 快进无法跳过的过场动画、游戏内 PC 设置菜单（F1 或 `Plus`+`Minus`）、Discord Rich Presence |
| **Mod** | 几乎所有模拟器能用的 Mod 在这里也能用，还原生支持 Forge 插件（见 [Mod](#mods)） |
| **金手指** | 几乎所有模拟器金手指代码同样可用，见 [金手指](#cheats) |

**如需 AMD FSR 4，请使用这个模块：https://github.com/Huss3A/mhgurecomp-fsr4-module**

<a id="requirements"></a>
## 运行环境要求

- 操作系统：Windows 10/11 64 位，或 glibc 2.39 及以上的 64 位 Linux。以下 Linux 发行版已验证可用（需支持 Vulkan）：
    - Ubuntu 24.04
    - Linux Mint 22
    - Debian 13
    - SteamOS 3.7
    - Arch
    - Fedora 40
- CPU：2014 年及以后的任意 CPU（需支持 AVX2）
- GPU：2016 年及以后的任意 GPU（需支持 Vulkan 1.2），显存至少 1 GB
- 内存：4 GB
- Android（实验性）：64 位 ARM 设备、Android 10 及以上、Vulkan 1.1 和一个手柄。见 [Android](#android)
- 《怪物猎人 Generations Ultimate》1.4.0 版的游戏文件。可从你的 Switch 或已打好补丁的 Ryujinx 中提取。
    - （Title ID `0100770008DD8000`，`main` 可执行文件的 Build ID 以 `FB08F1D20FD1204F` 开头）

**macOS 支持请关注 mhvuze 的 fork：https://github.com/mhvuze/MHGURecomp/releases**

<a id="installation"></a>
## 安装

[从 Releases 页面下载最新的预编译版本，务必选择与你平台对应的 ZIP 文件。](https://github.com/morerokk/MHGURecomp/releases)

你需要《怪物猎人 Generations Ultimate》1.4.0 的 `exefs` 和 `romfs` 文件夹。如果你来自 Ryujinx，可以右键游戏（确认已应用 1.4.0 升级补丁），选择「提取已合并补丁的游戏文件」。Yuzu 也有类似功能，也可以用其它工具提取。

用其它工具提取也可以，只要同时提取本体文件和 1.4.0 升级补丁即可。升级补丁的 `exefs` 和 `romfs` 文件应覆盖到本体文件之上。

1. 把发布包解压到任意位置，例如 `C:\Games\MHGURecomp\`。
2. 把游戏的 `exefs` 和 `romfs` 文件夹放进 `data` 子目录，结构应如下：

   ```
   MHGURecomp\
     mhgurecomp.exe
     mhgugame.dll
     (其它 .dll 文件)
     data\
       exefs\
         main
         main.npdm
         rtld
         sdk
         subsdk0
       romfs\
         nativeNX\
         (游戏 romfs 的其余内容)
   ```

   `exefs` 必须来自 1.4.0 升级补丁，`romfs` 必须是本体 romfs 叠加升级补丁后的合并结果。最终大约 35,500 个文件、12.3 GB。
3. 运行 `mhgurecomp.exe`。

<a id="staying-up-to-date"></a>
### 保持更新

版本发布可能比较频繁。想自动更新，就运行 `mhgurecomp-updater.exe`（Linux 上是 `mhgurecomp-updater`）。更新器支持手柄操作，可以放心把它当作主快捷方式，或添加为 Steam 非 Steam 游戏。

- 更新器始终检查 GitHub 上的最新正式版。偶尔会有预发布版，自动更新器不会提供，因为它们可能不稳定。
- 更新时只替换移植版本身的文件，`data`、`mods` 等其它文件夹全部保留。
- 自动更新行为可在设置中调整。
- 遇到问题时，`updater.log` 里有更详细的信息。

<a id="where-things-are"></a>
### 文件都放在哪

| 内容 | 位置 |
| --- | --- |
| 设置 | `mhgurecomp.ini`（需要重置设置时删除它即可） |
| 存档 | `%APPDATA%\MHGURecomp\save\`（Linux：`~/.local/share/MHGURecomp/save/`），或设置菜单里指定的存档文件夹（「Menu Options」标签页，对应 `mhgurecomp.ini` 的 `SaveLocation`） |
| 日志 | `log.txt`，提交 issue 时请附上此文件 |
| 截图 | `shots\`（按 F12） |
| Mod | `mods\`，每个 Mod 一个文件夹（见下文） |
| 引擎模块 | `engine_modules\`（见下文） |
| 金手指 | `cheats\` 下存放金手指代码的 `.txt` 文件（见下文） |
| 着色器缓存 | `cache\` |

要导入 Switch 上已有的存档，把 `system` 和 `system_backup` 文件放到 `%APPDATA%\MHGURecomp\save\save_0\`（Linux：`~/.local/share/MHGURecomp/save/save_0/`）。

<a id="android"></a>
### Android

**Android 版本仍处于实验阶段！** 你需要：

- 一台 64 位 ARM 处理器、Android 10 或更高版本的手机 / 平板 / Android TV 设备，GPU 驱动需支持 Vulkan 1.1（FSR 需要 Vulkan 1.2）。建议较新的中高端设备（骁龙 865 或更好）、6 GB 以上内存；NVIDIA Shield TV Pro 2019（3 GB）也能运行，狩猎时约 41–45 fps。
- 一个手柄（蓝牙或 USB），**没有触屏操作**。
- 约 13 GB 可用空间存放游戏文件（从其它文件夹导入时需要 26 GB）。

1. 从 [Releases 页面](https://github.com/morerokk/MHGURecomp/releases) 下载 `Android-MHGURecomp.<版本>.apk` 并在设备上打开。首次安装时 Android 会要求允许浏览器或文件管理器安装应用。
2. 把游戏的 `exefs` 和 `romfs` 文件夹放在设备上任意位置（例如 `Download` 目录或 SD 卡），两者放在同一个文件夹里。启动 **MHGU Recomp**，它会提示找不到游戏文件并提供 **Import game files（导入游戏文件）**。选择包含 `exefs` 和 `romfs` 的那个文件夹，应用会把它们复制到自己的目录（几分钟）。之后可以删除你放的那份副本。

   空间不够，或文件在 U 盘 / SD 卡上？改为选择 **Use where they are（就地使用）**：不复制任何文件，游戏直接从该文件夹读取，因此游玩时存储介质必须保持连接。Android 会要求为应用开启「所有文件访问权限」。使用大容量 U 盘时首次启动可能需要几分钟。
3. 也可以从 PC 复制：先启动一次应用（让它创建目录），用 USB 连接设备并选择 **文件传输**。在 PC 上打开设备存储，进入 `Android\data\io.github.morerokk.mhgurecomp\files\`，把游戏的 `exefs` 和 `romfs` 文件夹复制到其中的 `data` 目录：

   ```
   Android/data/io.github.morerokk.mhgurecomp/files/
     data/
       exefs/
         main
         (main.npdm, rtld, sdk, subsdk0)
       romfs/
         nativeNX/
         (游戏 romfs 的其余内容)
   ```

   如果 PC 上看不到 `files` 或 `data` 文件夹，重启设备后重新连接（或自行创建 `data`）。Android 11 及以上系统自带的文件管理器无法打开 `Android/data`，所以要用 PC。也可以用 [adb](https://developer.android.com/tools/adb) 在终端推送：
   `adb push exefs romfs /sdcard/Android/data/io.github.morerokk.mhgurecomp/files/data/`
4. 连接手柄，启动游戏。

所有内容都存放在这个 `files` 文件夹里，其结构与 PC 版的游戏目录一致：

| 内容 | 位置（相对于 `Android/data/io.github.morerokk.mhgurecomp/files/`） |
| --- | --- |
| 游戏文件 | `data/exefs/`、`data/romfs/` |
| 存档 | `save/save_0/` |
| 设置 | `mhgurecomp.ini`（或游戏内设置菜单：`Plus`+`Minus`） |
| 日志 | `log.txt` |
| Mod、金手指 | `mods/`、`cheats/` |
| 着色器缓存 | `cache/` |

设置菜单里有一个 **Android** 标签页（最后一个），用来处理设备文件管理器在 `Android/data` 下做不到的事：

- **Files folder（文件文件夹）：** 把应用的文件（设置、存档、Mod、金手指、截图、`log.txt`、`env.txt`）放到你指定的文件夹，而不是 `Android/data`，这样设备自带的文件管理器就能打开。应用会把文件复制过去（缺失的会补上；若该处文件比应用内的旧，例如在别处玩过之后的存档，会询问是否覆盖，被覆盖的保留为 `.bak`；游戏文件不会复制，改为就地使用；着色器缓存也不复制，会重新生成），然后关闭应用，需要重新启动。Android 会要求「所有文件访问权限」。**Use the app's folder（使用应用文件夹）** 会把文件搬回来，两种方式都有进度提示。首次启动时也会询问一次（重装后同样，因为会忘记该文件夹：重新选一次即可使用其中的内容；留在应用目录里的游戏文件会被卸载删除，需要重新导入）。如果启动时所选文件夹不可用（关闭了「所有文件访问权限」、文件夹被移动或删除、所在的盘不在了），应用会提示并让你重新选择或本次改用自带目录；此时选 **Use the app's folder** 会永久忘记该设置。
- **Import save（导入存档）：** 从设备任意位置选择 `system` 和 `system_backup` 文件。应用会复制进去，把当前存档备份为 `save/save_0.before-import-<日期>`，然后关闭；重新启动即可游玩。（通过 USB 也可以自己把这两个文件放进 `save/save_0/`。）
- **Export save（导出存档）：** 把存档的两个文件复制到你指定的文件夹，用于备份或迁移。
- **Save folder（存档文件夹）：** 把存档放在你指定的文件夹（即包含 `save_0` 的那个），方便同步软件在多台设备间保持一致：每台设备选同一个文件夹即可。由于应用要自行读写该目录，Android 会要求「所有文件访问权限」。按 Save 后重新启动应用。当前存档不会被移动：需要先用 **Export save** 把它放进该文件夹。**Use the app's folder** 可恢复默认。
- **Game files folder（游戏文件文件夹）：** 就地使用游戏文件（即首次启动时的 **Use where they are**），例如放在 U 盘或 SD 卡上。Android 会要求「所有文件访问权限」。按 Save 后重新启动应用。**Use the app's folder** 可恢复默认。
- **Import game files（导入游戏文件）：** 与首次启动时的导入相同（见上文），用于替换游戏文件，同时也会取代任何已设置的 Game files folder。
- **Import mod (zip)** 和 **Import mod (folder)：** 从设备任意位置选择 Mod 的 `.zip` 或文件夹，应用会放进 `mods/`。导入前会检查目录结构：游戏会在 Mod 文件夹内最多三层深处的 `romfs`、`exefs` 或 `nativeNX` 文件夹中查找文件。如果文件埋得更深（例如 zip 外面又套了几层文件夹），或补丁文件（`.pchtxt`、`.ips`）不在 `exefs` 文件夹里，会给出提示并在导入时提供修复（只移动文件，不修改内容）。完全不含这些文件夹的 zip 会被标记为「看起来不像 Mod」，但仍可强制导入。关闭并重新打开应用以加载 Mod。

FPS 计数器旁边有一个 **Battery indicator（电量指示）**（Graphics & Audio）：可关闭、显示在 FPS 计数器框内，或单独显示在一个框里。

Android 版菜单里没有 Restart（应用无法自行重启）：用 Exit game 退出后重新打开即可。从 PC 版迁移，复制 `%APPDATA%\MHGURecomp\save\save_0\`（Linux：`~/.local/share/MHGURecomp/save/save_0/`）里的内容；从 Switch 迁移则使用与 PC 版相同的文件。建议现在就把 `save/save_0/` 复制回 PC 作为备份。

Android 上的公共网络集会所只与其他 Android 玩家共享。想和 PC 上的朋友一起玩，所有人输入同一个匹配密钥（设置菜单 → Multiplayer）。

更新时直接把新版 APK 覆盖安装：游戏文件、存档和设置都会保留。**不要先卸载**，卸载会删掉整个 `files` 文件夹，包括游戏文件和存档。如果 Android 询问是否保留应用数据，打算重装就选「是」。

<a id="controls"></a>
## 操作

只要 SDL 支持，几乎所有手柄都能用。接了多个手柄时（例如 Steam Deck 又插了一个手柄），按一下你想用的那个手柄上的任意按键即可。如果确实想在非任天堂手柄上对调按键位置，可以打开 .ini 文件设置 `FaceButtons = Label`，不过更推荐装一个能对应按键提示的 Mod。

键盘和鼠标也已支持，而且实测相当可用。默认键位：

| 按键 | 对应的 Switch 按键 |
| --- | --- |
| W A S D | 左摇杆（按住左 Shift 走路） |
| 鼠标 | 视角 |
| 左键 / 右键 | X / A |
| 空格 / R 或中键 | B / Y |
| 滚轮 | 道具栏：向上 = 左边的道具，向下 = 右边的道具（狩猎中无需按住 L） |
| Q / E | L / R |
| Tab / T | ZL / ZR |
| Enter / Backspace | Plus / Minus |
| 方向键 | 十字键 |
| Ctrl / Alt | 左 / 右摇杆按下 |

可在设置菜单（F1）→ Controls → Keybinds 中修改，同一个动作最多可绑定 2 个按键。

Escape、Insert、F1 以及 F7 到 F12 被移植版本身占用，无法绑定。

有时游戏会要求键盘输入，例如给猎人起名或重命名套装。此时用键盘输入文字，`ENTER` 确认，`ESC` 取消。在联机大厅中可用 `/` 键自由聊天。

其它实用快捷键：

- F1：设置菜单
- Alt+Enter 或 F11：窗口 / 全屏切换
- F7：循环切换 MSAA
- F12：截图

<a id="settings"></a>
## 设置

键盘按 F1、或手柄按 `Plus`+`Minus`（`Start`+`Select`）打开设置菜单。

每个设置项也都写在 `mhgurecomp.ini` 里，上方有注释说明。详见 [docs/SETTINGS_UI.md](docs/SETTINGS_UI.md)。

<details>
<summary><b>全部设置项，按 <code>mhgurecomp.ini</code> 的分节排列</b></summary>


- `[Display]`：`Mode`（Borderless / Fullscreen / Windowed，无边框 / 全屏 / 窗口）、`Resolution`（分辨率）、`RenderResolution`（3D 渲染分辨率）、`AspectRatio`（Auto 跟随窗口：16:10 及更宽会铺满，更窄则按 16:10 加黑边）、`FOV`（1.0 = 游戏原始值）、`UIAnchor`（Center 在超宽屏上把 HUD 保持在中间 16:9 区域，Edges 把 HUD 分散到两侧）
- `[Anti-aliasing]`：`MSAA`（Off / 2x / 4x / 8x）、`FXAA`（On / Off）、`FXAAMode`（Original / 3_11：用 FXAA 3.11 替代 GU 自带的 FXAA，纹理更锐利；默认 Original）
- `[Upscaler]`：`FSR`（Off / On，默认 Off）、`FSRQuality`（NativeAA / Quality / Balanced / Performance / UltraPerformance）、`Sharpness`（锐度）。FSR 开启时会取代 MSAA 和 FXAA。详见 `docs/FSR-PORT.md`
- `[Graphics]`：`DrawDistance`（村庄和集会所里的人物在多远仍被绘制：1 = 游戏原始值，2 = 两倍，0.5 = 一半，0 = 不限制；最大 10）
- `[HDR]`：`HDR`（Off / On，默认 Off：在 HDR 显示器上输出原生 HDR10 或 scRGB，移植自本游戏的 RenoDX HDR Mod；需先在系统显示设置中打开 HDR）、`PeakBrightness`、`GameBrightness`、`UIBrightness`（单位 nit）、`ToneMapper`（Vanilla / None / RenoDRT）、`GammaCorrection`（Off / 2.2 / BT.1886）、`Exposure`、`Highlights`、`Shadows`、`Contrast`、`Saturation`、`HighlightSaturation`、`Flare`、`Bloom`、`UnclampedScene`、`HDRFormat`（仅 ini）。使用时请关闭 FSR。详见 [docs/HDR.md](docs/HDR.md)
- `[Performance]`：`FPS`（30 到 240）、`VSync`（On / Off；帧率高于显示器刷新率时请关闭）、`ShaderPrewarm`（On / Off：启动时在后台翻译游戏的所有着色器，减少物体首次出现时发黑的情况；首次启动在 logo 画面约需 20 秒，缓存文件夹约需 340 MB）。exe 旁边的 `pipelines.list` 列出了常用区域的着色器组合；开启预热后这些也会在后台准备好，于是首次进入这些区域不再出现表面短暂发黑。该文件仅在 MSAA Off 下制作，其余组合仍在首次需要时准备。录制方法见 [docs/PIPELINE_LIST.md](docs/PIPELINE_LIST.md)。`LoadingIndicator`（On / Off：游戏启动并准备着色器时右下角显示「Loading」框；仅 ini 可设，设置菜单中没有）
- `[Controls]`：`FaceButtons`（Position / Label，按位置 / 按标识）、`MenuConfirm`（设置菜单的确认键）、`BackgroundInput`（On / Off：游戏窗口在后台时手柄仍可用，例如前面开着 wiki；默认 On）、`ComboInputWindow`（Lenient / Strict：像狩猎笛 X+A 这类输入，游戏等待第二次按键的时长；默认 Lenient，在任何帧率下都相当于 30 fps 时的时长；Strict 是固定帧数，帧率越高越短）
- `[Mouse]`：`MouseSensitivity`（1 = 默认，范围 0.1 到 10）
- `[Multiplayer]`：`Port`、`Join`（局域网外主机的地址）、`Server`（互联网集会所的 hub 服务器：留空 = 默认，`Off` = 不用，或 `host[:port]`）、`Key`（匹配密钥：只有密钥相同的玩家才能看到彼此的集会所；留空 = 公开，Android 上公开仅指 Android 玩家之间）、`SyncSmallMonsters`、`ShareUrgentCredit`（默认 On：别人发布的紧急任务，只要你自己已解锁，完成后也算你完成）
- `[Monster HP]`：集会所任务中 1 到 4 人时怪物血量与部位血量（硬直、破坏、断尾）的倍率，以及按任务的例外设置（默认全为 1，即原版数值）
- `[Village Quests]`：`VillageQuestsInHub`（默认 On）、`HubHP`（默认 2.0：在集会所发布的村庄任务，怪物血量与部位血量先乘以此值，再乘 `[Monster HP]` 的倍率）
- `[Discord]`：`RichPresence`（默认 On：Discord 个人资料显示你所在的地点、正在狩猎的怪物和地图、集会所或任务中的人数；Discord 需在同一台电脑上运行）、`ShowHunter`（默认 On：同时显示猎人名字、HR 和武器类型）
- `[Bonus Content]`：`BonusContent`（默认 On），见下文
- `[Audio]`：`Volume`（0 到 100，整个游戏）、`MuteInBackground`（On / Off，默认 Off：游戏窗口在后台时静音）
- `[Application]`：`ConfirmExit`（关闭窗口前询问），以及设置菜单的 `Language`（English / Spanish）、`ButtonIcons`（Xbox / Switch / PlayStation）、`Theme`（Hunter 默认 / Gold / Blue，设置菜单配色）和 `MenuScale`（50 到 200 百分比），还有 `Updates`（Ask / Auto / Off，决定 `mhgurecomp-updater` 的行为，见「保持更新」）。用鼠标拖动设置菜单顶部（标签页）可移动它，拖右下角把手可调整大小；Menu Options > Attach menu 可让它复位。

</details>

<a id="multiplayer"></a>
## 联机

在局域网或 VLAN 内开箱即用，同一网络下的其它集会所会自动出现在列表里。

游戏还预置了我自己的 LDN 服务器（自建服务器所需的软件也包含在本仓库中）。默认情况下，用游戏内的「本地无线通信」选项就能看到其他在线玩家和集会所。

如果只想和固定好友或固定队伍玩，在 F1 菜单里设置一个匹配密钥。设置了相同密钥的玩家只能看到彼此。

想自建 LDN 服务器请看 [server/README.md](server/README.md)。如果连不上 hub 服务器，屏幕顶部会有提示。我会尽量让 LDN 服务器 7×24 小时在线。

也可以完全不用 LDN 服务器，直接和朋友联机：主机需要转发正确的端口（默认 39500 TCP/UDP），所有客户端在自己的 .ini 里配置主机的 IP 地址（`Join = xxx.xxx.xxx.xxx`）。

请选择「本地无线通信」联机选项，因为这个端口会把自己伪装成附近一台通过无线连接的 Switch。「在线」选项不可用，也没必要。

<a id="crossplay"></a>
### 与模拟器联机（实验性）

也可以和 Ryujinx / Ryubing，以及 suyu、yuzu、Eden、Citron 和其它保留了多人房间的分支玩家一起玩。这仍是实验性功能：已针对模拟器的服务器端软件做过测试，但还没有与真实模拟器玩家实际狩猎验证。出问题请附上 `log.txt` [提交 issue](https://github.com/morerokk/MHGURecomp/issues/new/choose)。

先了解几点：
- 跨平台联机在 `mhgurecomp.ini` 的 `[Multiplayer]` 节配置，不在 F1 菜单里。如果你的 .ini 来自旧版本、还没有下面这些设置，手动加上即可。
- 所有人都必须是游戏 1.4.0 版，模拟器玩家也一样。
- 集会所里一旦有模拟器玩家，本移植版的附加功能（小怪物同步、血量缩放）会关闭：只有本移植版的玩家能理解这些功能。

**简单做法：由一名本移植版玩家统管一切。** 主机开启游戏内置的服务器：

```ini
RyuServe = On        ; 供 Ryujinx / Ryubing 玩家使用（TCP 端口 30456）
RoomServe = On       ; 供 suyu、yuzu、Eden、Citron…… 玩家使用（UDP 端口 24872）
RoomPassword =       ; 可选：房间密码
```

这些服务器只在「本地无线通信」开放期间运行，所以主机照常创建集会所即可。要经由互联网联机，主机转发上述端口，或者所有人使用 Radmin 之类的 VPN。然后：
- **Ryujinx 玩家**把 LDN 服务器设为主机地址（端口 30456），在「本地游玩」中搜索集会所。
- **suyu / Eden / Citron 玩家**连接到主机 IP、端口 24872 的多人房间（若设了密码则一并输入）。
- **其它本移植版玩家**设置 `RyuServers = <主机地址>`，这样该集会所会出现在他们的「搜索集会所」里。

两个服务器都开启时，Ryujinx 玩家和房间玩家可以进入同一个集会所。

**使用已有的服务器：**
- `RyuServers = host[:port], ...`：这些 Ryujinx LDN 服务器的大厅会出现在「搜索集会所」里（默认端口 30456）。
- `RyuHost = host`：你创建的集会所建在该服务器上，于是上面的 Ryujinx 玩家也能加入。
- `RoomServer = host[:port]` 和 `RoomHost = On`：同上，但用于 suyu 风格的多人房间（默认端口 24872）。`RoomName` 是你在房间里的名字，`RoomPassword` 是房间密码。
- `RyuHost` 与 `RoomHost` 同时使用，可创建一个 Ryujinx 玩家和房间玩家都能加入的集会所。
- 请不要占用 Ryujinx 自家的公共 LDN 服务器，那是给 Ryujinx 用户用的。请自建 Ryujinx LdnServer，或直接用 `RyuServe`。

**注意事项：**
- 想和 Ryujinx 玩家组成私密小队，把 `RyuPassphrase` 设为 `Ryujinx-` 加恰好 8 位十六进制字符（例如 `Ryujinx-1a2b3c4d`），并让 Ryujinx 玩家输入同一个值。其它任何写法（包括打错字）都视为没有口令，意味着你的大厅是**公开的**。Ryujinx 的规则相同。
- 同时有 Ryujinx 玩家和房间玩家的集会所测试最少。如果出现异常（例如任务里互相看不见），试试只用 Ryujinx 玩家或只用房间玩家的集会所。
- 如果有人退出又重新加入跨平台集会所后出现奇怪现象，新建一个集会所。

<a id="bonus-content"></a>
## 附加内容

默认情况下，发布包的 `bonus` 子文件夹里含有一个带全部免费在线内容（活动任务、道具包、随从猫）的存档，游戏第二次启动时会被复制进你的存档。

不想要的话，设置 `BonusContent = Off`，或者不要在 `bonus` 子文件夹里放存档。也可以换成你自己的存档。注意：如果附加内容已经存在，移植版不会再尝试复制。

<a id="mods"></a>
## Mod

安装 Mod 只需把 Mod 文件夹放进 `mods\`，删除该文件夹即卸载。Mod 在启动时叠加到游戏之上。

- romfs Mod（替换或新增游戏数据的文件）在 Mod 文件夹内查找，也支持 `atmosphere\contents\0100770008DD8000\romfs` 这种布局。
- 当多个 Mod 携带同一个游戏归档（如 `resident_eng.arc`）时，只会应用每个 Mod 相对原游戏改动过的条目，因此修改同一归档中不同文件的 Mod 可以共存。如果两个 Mod 改了同一个条目，加载顺序靠后的胜出，日志也会说明（"changes ..., which an earlier mod changed too"）。Mod 按字母顺序加载。想自定义顺序，可创建 `mods\load_order.txt`，每行写一个 Mod 文件夹名：此时只加载列出的 Mod，且按该顺序。合并后的归档保存在 `cache\arcmerge\`。
- 支持不完整的 `.arc` 文件（即只含单个待替换条目的 `.arc` 也能用）。条目按内部名称和类型与游戏匹配，且归档版本必须与游戏一致（17）。如果一个归档完全不含游戏的任何条目，则整体替换该归档。
- 设置菜单的 **Mods** 标签页无需编辑文件即可完成上述操作：列出 Mod 文件夹、逐个开关、上下移动，按 Save 时写入 `mods\load_order.txt`（重启生效；之后新加的 Mod 也会加载，排在已列出的之后，直到你把它关掉；被关掉的 Mod 仍保留原有顺序位）。它还会比较各 Mod，列出修改相同游戏文件的那些（以及最终采用哪一个），并可按「改动文件多的优先」应用一个建议顺序。
- exefs 补丁（`.pchtxt`、`.ips` / IPS32）会应用到数据和代码上。游戏代码是预编译的，因此被补丁修改的函数会改由解释器执行（略慢，且仅限该函数）。Mod 自带的代码模块（`exefs\subsdk1` 等，与 [MH4U Port](https://github.com/Scrimas/MH4U-port-to-MHGU) 中一样）也会被加载并在解释器中运行。日志会记录打了什么补丁、加载了什么（`[mods]` 行）。
- Forge 插件（`romfs\nativeNX\plugins\` 下的 `.nro`）会被加载。Forge 自带的加载器（Forge 及带 Forge 插件的 Mod 里附带的 `exefs\subsdk9`）不需要，会被跳过：移植版自己运行插件。按 Insert 打开 Forge 的插件设置菜单（若 Mod 包含了 Forge 的文件，也可用 Forge 自身 `config.ini` 里的按键，该文件还能设置 `[log] level`）；只有手柄时，用设置菜单 Mods 标签页底部的 **Open the Forge menu**。菜单内可用鼠标、键盘或手柄操作。用手柄时，游戏菜单里的取消键（当 Forge 窗口里已无可取消的内容时）或 Start + Back 可关闭它。菜单打开期间游戏收不到手柄输入。窗口位置保存在 `forge_imgui.ini`。
- 给 Mod 作者：除 Forge 的 API 外，移植版还向 Mod 开放了鼠标接口：`forge_input_getMouse`（1280x720 屏幕上的指针位置与按键）、`forge_input_getMouseMove`（移动量，即使狩猎视角占用鼠标时也有）和 `forge_input_setMouseFree`（Mod 自己的菜单打开时不捕获鼠标）；以及键位接口：`forge_input_setKeybind`（临时为某个 `[Keybinds]` 行换一组按键，不改动玩家的设置）、`forge_input_getKeybind`、`forge_input_getModKeybind`（某个 Mod 为该行设置的值，如有）和 `forge_input_getKeyPressed`（刚按下的键名，供 Mod 自己的键位菜单使用）。设置菜单会显示哪些行被 Mod 占用。见 `runtime/forge.c`。
- 不需要任何分辨率、帧率上限或联机修复类 Mod，这些功能已内置于本移植版。

**Mod 下载来源：**

- [MHGURecomp-Mods 仓库](https://github.com/Oddity-git/MHGURecomp-mods)
- [MHGU GameBanana](https://gamebanana.com/mods/games/17088)

**Mod 制作资料：**
- [MHGU-Modding Wiki](https://github.com/RTHKKona/MHGU-Modding/wiki)
- [Fexty's Forge](https://github.com/Fexty12573/forge)

<a id="engine-modules"></a>
## 引擎模块

引擎模块是扩展移植版本身、而非扩展游戏的原生程序（例如换一个超分算法）。它们不是 Mod，也不是 Forge 插件，并且**与游戏拥有同等权限，所以只安装你信任的模块**。默认情况下什么都不会加载：把模块文件夹放进 `engine_modules\`，再把文件夹名单独写一行到 `engine_modules\enabled.txt` 中。`log.txt` 会列出实际加载了什么。模块作者请看 [docs/ENGINE-MODULES.md](docs/ENGINE-MODULES.md)。

<a id="cheats"></a>
## 金手指

可在 F1 菜单里配置金手指，也可以手动把 .txt 文件放进 `cheats/` 子目录。

每条金手指默认都是启用的，可以在 F1 菜单中关闭。GU 的任意金手指代码都应当可用，用法与模拟器相同。一个文件可放任意多条，每条以方括号中的名字开头：

```
[Skill points x2]
04000000 000DFAB4 E1A00080
```

- 在设置菜单（F1）的 Cheats 标签页可逐条开关，按 Save 立即生效。新增、修改或删除的金手指文件，在下一次打开设置菜单时生效。
- 想停用某个文件又不想删掉它，把文件名以 `_` 开头即可。
- 修改游戏代码的金手指也能用，但每用一条都可能带来*极*轻微的性能损失。对绝大多数金手指代码来说无关紧要。
- `log.txt` 会列出已加载的金手指，以及读取失败的代码。
- `extras\cheats\` 里有一些示例。[更多代码见 MHGU Modding Wiki 的 Cheat Codes 页面。](https://github.com/RTHKKona/MHGU-Modding/wiki/Cheat-Codes)
    - 本仓库中的 Valor Sheathe（勇气风格收刀）金手指，只有在安装了 MHGU Rebalanced 时才起作用。
- **请**在联机时告知其他玩家你正在使用金手指、以及用了哪些代码。友善一点。

<a id="building-from-source"></a>
## 从源码构建

构建过程会用你自己那份游戏重新编译游戏代码。本仓库不包含任何游戏代码或数据，因此需要先提取好游戏文件（见上文）。

<a id="tools-windows"></a>
### 1. 工具（Windows）

1. 把 [MSYS2](https://www.msys2.org/) 安装到 `C:\msys64`。
2. 在 **MSYS2 UCRT64** 终端里安装编译器与依赖库：

   ```bash
   pacman -S --needed make git diffutils \
     mingw-w64-ucrt-x86_64-clang mingw-w64-ucrt-x86_64-lld mingw-w64-ucrt-x86_64-pkgconf \
     mingw-w64-ucrt-x86_64-sdl3 mingw-w64-ucrt-x86_64-shaderc mingw-w64-ucrt-x86_64-nasm \
     mingw-w64-ucrt-x86_64-vulkan-headers mingw-w64-ucrt-x86_64-vulkan-loader \
     mingw-w64-ucrt-x86_64-vulkan-memory-allocator
   ```

   这里没有安装 FFmpeg（用于播放游戏过场影片）：首次构建会下载其源码，只把影片需要的那一小部分编译进可执行文件（见下文「FFmpeg」）。

3. 安装 Windows 版 [Python](https://www.python.org/) 3.10 或更高版本。然后在仓库目录的命令提示符中创建工具的虚拟环境（Makefile 会在 `tools\venv` 存在时使用它）：

   ```bat
   py -3 -m venv tools\venv
   tools\venv\Scripts\pip install -r tools\requirements.txt
   ```

<a id="recompile-and-build"></a>
### 2. 重编译并构建

在 UCRT64 终端中进入仓库目录，并准备好存放 `exefs\` 和 `romfs\` 的游戏文件夹（结构同[安装](#installation)一节）：

```bash
make gen GAME=/c/path/to/game      # 把游戏代码翻译为 C，输出到 generated/（约 300 MB）
make -j4 GAME=/c/path/to/game      # 编译全部内容到 build/
```

首次完整构建耗时较长（4 核 Haswell 上 `-j4` 约 8 分钟；核心更多可调高 `-j`）。之后的构建只重新编译改动过的部分。

`make` 会把 `build\` 变成一个可直接运行的游戏目录，且不会往里放别的东西（编译器自身的文件放在 `obj\`）：
- `mhgurecomp.exe`，运行时；
- `mhgugame.dll`，重编译后的游戏代码；
- 它们所需的 MSYS2 DLL；
- `data\exefs` 和 `data\romfs`，是指向你游戏文件的硬链接，因此不额外占用磁盘空间。

想从别的目录运行，把 `build\` 里的内容复制过去；更新时再覆盖一次即可（若 `data\` 已存在可跳过）。构建产物绝不包含设置、缓存、Mod 或日志，所以你的 `mhgurecomp.ini` 等文件会原样保留。也可以运行 `run-game.bat`：它启动 `build\mhgurecomp.exe`，并把设置、缓存、`mods\` 和 `log.txt` 放在 `run\`（即 `MHGU_HOME`）里，保持 `build\` 干净。直接运行 `build\mhgurecomp.exe` 也行，但那样会把上述文件写进 `build\`。

常用目标与选项：

- `make test-lift`：用 Unicorn CPU 模拟器对游戏数千条指令校验重编译器的正确性。
- `make clean`：删除编译产物（`obj\` 和 `build\` 里的程序文件），保留 `build\data`。
- `GENARCH=-march=x86-64-v2`：不使用 AVX2 编译游戏代码，供较老的 CPU 使用。未经测试。
- `FFMPEG=system`：链接系统的 FFmpeg 库，而不是自行构建（见下文）。
- Linux：`SDL3=system`、`SHADERC=system`：链接系统的 SDL3 / shaderc，而不是自行构建（见 Linux 一节）。

<a id="ffmpeg"></a>
### FFmpeg

游戏的过场影片是 H.264 视频 + AAC 音频的 MP4 文件。首次构建会下载 FFmpeg 源码（`third_party/ffmpeg/`，固定版本并校验 SHA-256），只把 MP4 读取器和这两个解码器编译到 `obj/` 并链接进可执行文件。无需安装或附带 FFmpeg 的任何东西，Linux 版在任意发行版上都能运行，无论系统装了哪个版本的 FFmpeg（或干脆没装）。这需要 `curl`，以及为 FFmpeg 的 x86 快速汇编准备 `nasm`（没有它 FFmpeg 会用纯 C，对这些影片也足够快）。一次性耗时几分钟。FFmpeg 采用 LGPL 2.1，其许可证会放进 `build/licenses/`。

`make FFMPEG=system` 改为链接系统的 avformat / avcodec / avutil（FFmpeg 5.1 或更高），与发行版打包方式一致；这样构建出的程序只能搭配该版本的 FFmpeg 运行。

<a id="making-a-release"></a>
### 制作发布版

<details>
<summary>给维护者：构建并发布一个版本</summary>

`make dist VERSION=<发布标签>` 会以该版本号构建全部内容并打包供 GitHub 发布：

```bash
git fetch --tags                          # （让两次发布之间的构建能知道上一个版本）
make dist VERSION=0.10.4 BONUS=<附加存档 system 文件的路径>
```

Windows 下会生成 `dist\Windows-MHGURecomp.0.10.4.zip`；Linux 下（或在 WSL 中加 `B=build-linux O=obj-linux`）生成 `dist/Linux-MHGURecomp.0.10.4.tar.gz`，其中程序的可执行权限会保留。每个压缩包内含一个文件夹，里面有 `mhgurecomp(.exe)`、`mhgugame.dll` / `.so`、`mhgurecomp-updater(.exe)`、随附的 DLL、`licenses\`、`bonus\system`（来自 `BONUS`，没给就留空），以及空的 `data\`、`mods\` 和 `cheats\` 文件夹；绝不会包含游戏文件，也不会包含构建目录里的设置、缓存或 Mod。`make dist` 会打印每个归档的 SHA-256。如果 `tools/gen.py` 或其它翻译器源码在上次 `make gen` 之后有改动，它会中止：先重新执行 `make gen`。

Windows 上如果安装了 Android SDK（见 [docs/research/android.md](docs/research/android.md)），`make dist` 还会额外生成 `dist\Android-MHGURecomp.0.10.4.apk`：仅 arm64，内含 `pipelines.list`、`licenses` 和附加存档，并用发布密钥签名。`ANDROID_DIST=` 可跳过。Android 只允许安装与已装应用用同一密钥签名的更新，所以每次发布都必须用到该密钥：`%USERPROFILE%\.android\mhgurecomp-release.keystore`，以及同目录下 `mhgurecomp-release.keystore.pass` 里保存的密码。两者都要备份，并复制到每一台负责发布的电脑。密钥不存在时 `make dist` 会中止，绝不会自动生成新密钥（换密钥意味着玩家必须先卸载，而卸载会删掉游戏文件和存档）。`make PLATFORM=android release-key` 可以生成一次。

把归档（以及 APK）上传到一个标签名与该版本号完全一致的 GitHub release（`0.10.4`，不要带 `v`），作为普通发布而非预发布。更新器只看 GitHub 的「latest」发布，把其标签与自身版本按数字比较（0.10.10 比 0.10.9 新），并挑选以 `Windows-`（`.zip`）或 `Linux-`（`.tar.gz`，否则 `.zip`；0.11.4 之前的名称是 `ArchLinux-`）开头的资源。GitHub 会记录每次上传的 SHA-256，更新器会校验。想暂时拦下一个有问题的版本，把它设为草稿或预发布即可：更新器会把上一个版本视为最新。

版本号来自 `git describe --tags`。不恰好落在标签上的构建（`0.10.3-4-gabc1234`）永远不会自我更新，因此开发版不会被正式版覆盖（`--update-force` 可强制）。测试更新器可用：`--update-no-launch`（之后不启动游戏）和 `MHGU_UPDATE_API=<url>`（换一个「最新发布」地址）。

`make` 会把一份拷贝必须携带的全部许可证放进 `licenses\`：本项目的 `LICENSE.txt`、`THIRD_PARTY_NOTICES.txt`（编译进来的代码）、FFmpeg 的许可证，以及 Windows 上随附 DLL 背后的 MSYS2 软件包和所链接库的许可证。`licenses\README.txt` 列出这些库的版本与确切源码位置，并包含其中 LGPL DLL（libiconv，SDL3 会用到）的源码书面提供邀约：谁发布版本，谁就要履行该邀约，因此请把那些源码保存三年（文件里给出的 MSYS2 地址是其中一份副本）。

exe 首次启动会创建 `mods`、`cheats` 文件夹和 ini 文件，玩家再按上文说明放入自己的 `data\`。

</details>

<a id="linux"></a>
### Linux

发布版包含原生 Linux 构建（Windows 版也能在 Proton / Wine 下运行）。当 `uname -s` 不是 Windows 时，Makefile 会选用 `runtime/platform/linux.c`，其余部分共用。除 `make`、`git`、`clang`、`lld` 和 Python 3.10 及以上之外，还需要：

- Vulkan 加载器与头文件，以及构建 FFmpeg 用的 `curl` 和可选的 `nasm`（见上文「FFmpeg」；不需要系统 FFmpeg 包）；
- `cmake`，以及 SDL 在桌面上所需组件的开发文件：X11（含 Xcursor、Xext、Xfixes、Xi、Xrandr、Xss、Xtst）、Wayland（wayland-protocols、libxkbcommon、libdecor）、PipeWire、PulseAudio、ALSA、libudev 和 D-Bus。与 FFmpeg 一样，首次构建会下载固定版本的 SDL3 和 shaderc（含 glslang、SPIRV-Tools）到 `third_party/`、校验 SHA-256 后静态链接，这样游戏在没有这些库的发行版上也能运行（Ubuntu 24.04 就没有 SDL3），而发布版除 glibc、libstdc++ 和 Vulkan 加载器外别无所求。SDL 运行时仍会从系统加载 X11 / Wayland 和音频服务；如果系统装了同版本或更新版本的 SDL3（新手柄支持、修复等），游戏会优先使用它：`log.txt` 会说明用的是哪个（`[ui] SDL ...`），`MHGU_SDL=bundled` 可强制使用内置版本。这一步一次性耗时几分钟；若 SDL 没找到其中某项，构建会中止（`SDL3_NEED`）。`make SDL3=system SHADERC=system` 则改为链接系统的 `libSDL3.so.0` / `libshaderc_shared.so.1`，与发行版打包方式一致；
- `vk_mem_alloc.h`（3.4.0）放在 `third_party/vk_mem_alloc/`，Makefile 已把该目录加入头文件搜索路径（发行版若把头文件装到编译器默认路径，效果相同）；
- `zenity` 或 `kdialog`，用于致命错误弹窗。两者都没有时，错误信息照常输出到终端和 `log.txt`；
- 更新器：构建需要 zlib 头文件，运行时需要 `libcurl.so.4`（curl），SteamOS 和常见桌面发行版都有。它自行加载 libcurl，因此缺少时更新器只是直接启动游戏。

```bash
python3 -m venv tools/venv && tools/venv/bin/pip install -r tools/requirements.txt
make gen GAME=../mhgu/game       # 同上：存放 exefs/ 和 romfs/ 的文件夹
make -j8 GAME=../mhgu/game
cd build && ./mhgurecomp
```

`build/` 与 Windows 上一样成为游戏目录：`mhgurecomp`、含重编译游戏代码的 `mhgugame.so`、作为游戏文件硬链接的 `data/`，别无他物；ini、缓存和 `mods/` 在运行时写到它们旁边（`MHGU_HOME=<文件夹>` 可改到别处）。存档放在 `$XDG_DATA_HOME/MHGURecomp/save`，默认为 `~/.local/share/MHGURecomp/save` —— 也就是 Windows 版在 `%APPDATA%` 下使用的目录，结构相同，所以跨平台搬存档只需复制 `save_0`。

在 Windows 上也可以用 WSL 里的 Arch Linux 构建 Linux 版（`wsl --install -d archlinux`），直接基于 Windows 的检出目录，输出到独立文件夹以免干扰 Windows 构建：

```bash
pacman -Syu --needed make git clang lld python cmake vulkan-headers vulkan-icd-loader nasm vulkan-swrast \
    libx11 libxcursor libxext libxfixes libxi libxrandr libxss libxtst wayland wayland-protocols libxkbcommon \
    libdecor pipewire libpulse alsa-lib systemd-libs dbus
mkdir -p /usr/local/include/vma && cp /mnt/c/msys64/ucrt64/include/vma/vk_mem_alloc.h /usr/local/include/vma/
make -j16 B=build-linux O=obj-linux     # 在仓库目录下，路径形如 /mnt/c/...
```

Arch 没有 `vk_mem_alloc.h` 的包，直接用 Windows 构建所用的 MSYS2 版（3.4.0）。`build-linux/data` 里可以放指向游戏文件的链接（`ln -s /mnt/c/.../exefs build-linux/data/exefs`，`romfs` 同理，再 `touch build-linux/data/.complete`），不必再复制一份。它也能在 WSLg 窗口里运行，只是很慢：WSL 自带的 Vulkan 驱动（dzn，基于 Direct3D 12 的 Vulkan）无法创建渲染器所需的管线布局，所以要改用 Mesa 的软件驱动 `VK_DRIVER_FILES=/usr/share/vulkan/icd.d/lvp_icd.json`。WSLg 无法捕获鼠标（点击仍可当作按键），截图在那里是全黑的。

<a id="repository-layout"></a>
## 仓库结构

| 文件夹 | 内容 |
| --- | --- |
| `tools/` | 重编译器：`lifter.py`（ARM 转 C）、`neon.py`（NEON / VFP）、`gen.py`（整模块生成）、`nso.py`，以及测试与研究工具 |
| `runtime/` | 宿主侧：CPU 状态、内核与线程、Switch 服务（`services/`、`hle/`）、网络（`net/`）、基于 Vulkan 的 NVN 图形 API（`nvn/`）、设置、输入、Mod |
| `updater/` | `mhgurecomp-updater`：把 GitHub 最新发布版安装到游戏目录，然后启动游戏 |
| `docs/` | `STATUS.md`：进度、设计说明、逆向工程发现、调试选项 |
| `android/` | Android 应用：manifest、Java Activity 与 APK 构建（`apk.mk`） |
| `server/` | 联机用的 hub（LDN）服务器，见 [server/README.md](server/README.md) |
| `tests/` | 纯宿主测试（设置、设置菜单、翻译），不需要游戏文件 |
| `third_party/` | 内建库的固定版本源码（SDL3、shaderc、FFmpeg、ImGui、FSR） |
| `extras/` | `cheats/`：玩家可复制到自己 `cheats` 文件夹的金手指文件；`pipelines.list` |

<a id="license"></a>
## 许可证

MHGU Recomp 自身代码采用 MIT 许可证（`LICENSE`）。它建立在 LAS Recomp 和 Forge 的代码之上，并捆绑了 cimgui、Dear ImGui、AMD FidelityFX SDK（FSR 3.1）和 FSR-Vulkan，这些同样都是 MIT 许可证：见 `THIRD_PARTY_NOTICES`。本许可证**不**覆盖游戏及其代码，包括构建产生的重编译游戏代码（`mhgugame.dll` / `mhgugame.so`）。

<a id="legal"></a>
## 法律声明

本项目与 Capcom 或任天堂均无关联，也未获其认可。Monster Hunter 是 Capcom 的商标。本仓库不含任何游戏代码、数据或密钥；构建时从你提供的一份拷贝中读取。请通过购买正版支持开发者。
