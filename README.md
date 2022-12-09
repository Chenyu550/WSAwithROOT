### 注意

这不是我的作品，这是我从`别人的`[存储库](https://github.com/LSPosed/MagiskOnWSALocal)里克隆过来的，来以防万一原库被封禁无法访问

# WSA 上的 Magisk（包括 Google Apps）

:warning: 对于 fork 开发人员：请不要使用 GitHub Actions 进行构建，因为 GitHub 会根据此上游存储库计算您的 fork GitHub Actions 使用情况，这可能会导致此上游存储库被 GitHub 工作人员禁用，例如 [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA)，因为有许多分叉构建 GitHub Actions，并针对此上游存储库计算分支的 Action 使用情况。

## 支持从这些系统生成（不支持Windows）

- Linux（x86_64 或 arm64）

    需要以下依赖项：`setools lzip wine patchelf e2fsprogs aria2 python3 attr`

    需要使用 `winetricks` 安装以下组件： `msxml6`

    使用 python3 库`requests`。

    Python 版本 ≥ 3.7。
  - 推荐使用
    - Ubuntu（您可以使用 [WSL2](https://apps.microsoft.com/store/search?publisher=Canonical%20Group%20Limited)）

        开箱即用。
        
    - Debian（您可以使用 [WSL2](https://apps.microsoft.com/store/detail/debian/9MSVKQC78PK6)）

        需要将 `contrib` 源添加到源列表以安装 winetricks。

    - OpenSUSE（您可以使用 [WSL2](https://apps.microsoft.com/store/search?publisher=SUSE)）

        开箱即用。

    `run.sh` 将自动处理所有依赖项。

    无需键入任何命令。
    
  - 其他发行版

    手动安装依赖项。

    使用命令行程序“build.sh”。

## 特征

- 在几分钟内点击几下即可集成 Magisk 和 GApps
- 使每个构建保持最新
- 同时支持 ARM64 和 x64
- 支持除 aroma 之外的所有 OpenGApps 变体（aroma 不支持 x86_64，请使用 super 代替）
- 删除亚马逊应用商店
- 修复 VPN 对话框不显示的问题（使用 [VpnDialogs](https://github.com/LSPosed/VpnDialogs) 应用程序）
- 添加设备管理功能
- 无人值守安装
- 在 Windows 11 中自动激活开发者模式
- 更新到新版本，同时使用一键式脚本保留数据
- 合并所有语言包
- 支持管理开始菜单快捷方式（手动安装[WSAHelper](https://github.com/LSPosed/WSAHelper/releases/latest)使用此功能）

## 文字指南

1. 点个star（如果你喜欢）
1. 克隆repo到本地
   - 运行 `cd 脚本`
   - 如果您想使用 CLI，然后运行 `./build.sh --help`（可选）以获取用法。
2. 在脚本目录下运行`./run.sh`。
3. 选择 WSA 版本及其架构（主要是 x64）。
4. 选择Magisk的版本。
5. 选择你要安装的GApps品牌
   - OpenGApps

        选择您喜欢的 [OpenGApps 变体](https://github.com/opengapps/opengapps/wiki#variants)。
   - MindtheGapps

       我们没有其他变体可以选择。
1. 选择root解决方案（none表示没有root）
1. 如果您是第一次运行脚本，需要一些时间才能完成。脚本完成后，将在 `MagiskOnWSALocal` 文件夹中生成两个名为 `output` 和 `download` 的新文件夹。转到“输出”文件夹。在步骤 3 中运行 `./run.sh` 脚本时，如果您为 `Do you want to compress the output?` 选择 `Yes`，那么在 `output` 文件夹中，您将看到一个名为 `WSA-with -magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly` 否则会有包含`WSA-with-magisk-stable-MindTheGapps_2207.40000.8.0_x64_Release-Nightly` 的文件夹。如果有文件夹，请打开它并跳至第 10 步。 
注意：压缩文件的名称或在“输出”文件夹中生成的文件夹可能与您不同。这将取决于执行 ./run.sh 时所做的选择
1. 解压缩压缩文件并打开文件解压缩后创建的文件夹。
1. 在这里找到文件 `Run.bat` 并运行它。
    - 如果您以前安装过 MagiskOnWSA，它会在**保留所有用户数据**的同时自动卸载前一个并安装新的，所以不用担心您的数据。
    - 如果您安装了官方 WSA，则应先将其卸载。 （如果你想保留你的数据，你可以在卸载前备份`%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache\userdata.vhdx`，安装后恢复。）（如果你想恢复图标到开始菜单，请安装并使用[WSAHelper](https://github.com/LSPosed/WSAHelper/releases/latest)。
    - 如果弹出窗口消失**没有询问管理员权限**并且 WSA 没有成功安装，您应该以管理员身份手动运行“Install.ps1”：
        1. 按 `Win+x` 并选择 `Windows终端(管理员)`
        2. 输入`cd "{X:\path\to\your\extracted\folder}"`并回车，记得把`{X:\path\to\your\extracted\folder}`替换掉`{}`，例如 `cd "D:\wsa"`
        3. 输入 `PowerShell.exe -ExecutionPolicy Bypass -File .\Install.ps1` 然后按 `Enter`
        4. 脚本将运行并安装WSA
        5. 如果这个解决方法不起作用，说明您的 PC 不支持 WSA
1. Magisk/Play商店将会出现。通过安装启用 Zygisk 的 LSPosed-zygisk 或 Riru 的 LSPosed-riru 享受吧！

## 常见问题

- 我可以删除已安装的文件夹吗？

    不。
- 如何将 WSA 更新到新版本？

    删除“下载”文件夹
    重新运行脚本，替换之前安装的内容并重新运行“Install.ps1”。别担心，您的数据将被保留。
- 如何从 WSA 获取 logcat？

    `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalState\diagnostics\logcat`
- 如何将 Magisk 更新到新版本？

    执行与更新 WSA 相同的操作
- 如何通过安全网？

    像所有其他模拟器一样，没办法。
- 未启用虚拟化？

    `Install.ps1` 帮助您启用它（如果未启用）。重新启动后，重新运行“Install.ps1”以安装 WSA。如果仍然无法正常工作，则必须在 BIOS 中启用虚拟化。这是一个很长的故事，所以向百度寻求帮助。
- 如何将系统重新挂载为可读写？

    在 WSA 中没有办法做到，因为它被 Hyper-V 安装为只读。您可以通过制作 Magisk 模块来修改系统。或者直接修改`system.img`。向百度寻求帮助。
- 我不能`adb connect localhost:58526`

    确保开发者模式已启用。如果问题仍然存在，请在设置页面上检查 WSA 的 IP 地址并尝试`adb connect ip:5555`。
- Magisk 在线模块列表为空？

    Magisk 主动删除了在线模块存储库。您可以在本地或通过 `adb push module.zip /data/local/tmp` 和 `adb shell su -c magisk --install-module /data/local/tmp/module.zip` 安装模块。
- 我可以使用 Magisk 23.0 稳定版或更低版本吗？

    不可以。Magisk 存在一些错误，无法在 WSA 上运行。 Magisk 24+ 已修复它们。所以你必须使用 Magisk 24 或更高版本。
- 我怎样才能摆脱 Magisk？

    选择“无”作为root解决方案。
- 如何安装自定义 GApp？

    [教程](./Custom-GApps.md)
- 在哪里可以下载 MindtheGapps？

    您可以从这里下载 [MindtheGapps](https://androidfilehost.com/?w=files&flid=322935) ([镜像](http://downloads.codefi.re/jdcteam/javelinanddart/gapps))

    请注意，没有 x86_64 预构建，因此您需要自己构建它 ([存储库](https://gitlab.com/MindTheGapps/vendor_gapps))。
- 我可以将 OpenGApps 切换到 MindTheGapps 并将用户数据保留在以前的版本中吗？

    不可以。您应该在更改 GApps 的源后擦除数据。否则，您会发现无法识别已安装的 GApp。

## 友情链接

- [StoreLib](https://github.com/StoreDev/StoreLib)：用于下载WSA的API
- [Magisk](https://github.com/topjohnwu/Magisk): 安卓上最著名的root解决方案
- [开放GApps项目](https://opengapps.org)：最著名的 Google Apps 软件包解决方案之一
- [WSA-Kernel-SU](https://github.com/LSPosed/WSA-Kernel-SU) 和 [kernel-assisted-superuser](https://git.zx2c4.com/kernel-assisted-superuser/ ): 用于调试 Magisk 集成的内核 `su`
- [WSAGAScript](https://github.com/ADeltaX/WSAGAScript): 第一个用于 WSA 的 GApps 集成脚本
