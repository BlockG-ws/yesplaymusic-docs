> 建议您提问前查阅 [issues](https://github.com/qier222/YesPlayMusic/issues) 和 [discussions](https://github.com/qier222/YesPlayMusic/discussions)。

>  💡 本文收集了一些群中常问的问题。你可以使用浏览器的页面内查找（tip：按 `Ctrl` + `F`，或旁边的侧边栏，以快速找到问题。

## 项目 Demo 无法登录、无法查看任何歌单信息

网易云端似乎不欢迎官方实例使用 API，因此阻挡了从我们实例送出的请求。请自行参考 [帮助文件](https://github.com/qier222/YesPlayMusic#%EF%B8%8F-%E9%83%A8%E7%BD%B2%E8%87%B3-vercel) 部署实例。

## 应用工作不正常，如何卸载重装客户端？

按 <kbd>F12</kbd> 打开控制台，输入 `resetApp()`，再重启客户端，即可重置客户端。

## 应用显示 `Error: listen EACCES: permission denied 0.0.0.0:10754`

您可以先尝试重启 YesPlayMusic。如果还是不行，请检查 10754 端口被谁占用。若未知占用者是哪个进程，重启设备亦不失为一个好方法。

## 应用显示 `Error: The specified module could not be found.` 如何处理？

安装 Microsoft Visual C++ Redistributable packages for Visual Studio 2015, 2017, 2019, and 2022 Runtime 即可: <https://docs.microsoft.com/zh-cn/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022>

## 应用无法正常加载？

<img src="https://user-images.githubusercontent.com/28441561/157833433-fdcdd4bd-bd37-449d-86eb-d8c4d415529b.png" alt="应用无法正常加载的画面" width="800px"></img>

您可以尝试：

- 重新启动客户端
- 更换 DNS 服务器（如 1.1.1.1 、 114.114.114.114 等）
  - [如何更改DNS服务器？](https://adguard-dns.com/zh_cn/public-dns.html)
- 关闭现有的 UnblockNeteaseMusic 服务实例（如路由器和本地存在的服务）

如果你有使用 OpenWrt 的话，那你很有可能有开启这个模组（功能）。需要先关起来才可以使用 YesPlayMusic（感谢 Rio 朋友提供的截图！）：

<img src="https://user-images.githubusercontent.com/28441561/173991992-94805179-5214-4237-946e-1239e8785197.jpg" alt="OpenWrt “解锁网易云灰色音乐” 模组关闭指引，credit: Rio" width="800px"></img>

## 有计划支持 桌面歌词 / 状态栏歌词吗？

因为之前的版本出现了问题被移除，且不符合 YesPlayMusic 的设计目标，因此暂无计划支持。

您可以使用 [YesPlayMusicOSD](https://github.com/shih-liang/YesPlayMusicOSD) 这个 fork 版本。（许久未更新）

如果您正在使用Windows 10/11，可以尝试 【[热词](https://www.microsoft.com/store/productId/9MXFFHVQVBV9)】这个应用，其在 [Github](https://github.com/cnbluefire/HotLyric) 上开源。

或者，尝试【[Lyricify](https://github.com/WXRIW/Lyricify-App)】，并参考[设置教程](./Lyricify-设置教程)。

如果您正在使用 Linux，可以尝试 【[OSDLyrics](https://github.com/osdlyrics/osdlyrics)】，并搭配 [Revincx 的 Fork](https://github.com/Revincx/YesPlayMusic) 使用。

> :warning: 如果要使用“热词”或”Lyricify“，请使用**最新Release版本**，Actions自动构建版会有问题。

## M1 芯片的 Mac 运行时提示已损坏怎么办？

将 YesPlayMusic 安装至 `/Applications` 后，在终端里执行
`xattr -r -d com.apple.quarantine /Applications/YesPlayMusic.app` 就可以了。

> credit: [#297 (comment)](https://github.com/qier222/YesPlayMusic/issues/297#issuecomment-782555219)

## 有计划支持本地音乐播放功能吗？

暂时无计划，但是未来可能会增加这个功能。

## 为什么有时候播放的歌曲跟歌曲名对不上？

你播放的可能是网易云灰色的歌曲。项目使用了 [UnblockNeteaseMusic](https://github.com/UnblockNeteaseMusic/server) 解锁灰色歌曲，
由于技术限制，可能会匹配到错误的歌曲。

> 👉🏻 据开发团队的观察，在歌曲进度条走完后的切歌也会出现这个情况。目前可以等修复。

## 有计划支持移动端吗？

暂无计划支持移动端，也无计划做安卓或 iOS 客户端。

目前网页端支持 PWA ，可以通过浏览器访问 demo（已不可用） 等实例安装。
目前移动体验不太好，之后可能会有移动适配版放出，敬请期待。

> 📦 正在开发的YesPlayMusic 2.0 对移动端作了比较好的适配。

> 📎 （由 GrassBlock 部署）第三方的移动端网页适配版：<https://ypm-lab-m.vercel.app/> （credit: [pr#1248](https://github.com/qier222/YesPlayMusic/pull/1248)

## 支持下载MP3文件吗？

因版权疑虑，不支持下载MP3文件。有此需求可以另去它处。

## 缓存文件存储位置在哪？我要怎么样清除缓存？

根据 Electron 文档，缓存存储在：

- Windows: `%APPDATA%` 中
- Linux: `$XDG_CONFIG_HOME` 或 `~/.config` 中
- macOS: `~/Library/Application Support` 中

你可以在应用的设置里清除缓存，或按 <kbd>F12</kbd> 启动控制台，执行 `resetApp()` 来重置应用。

## Windows 系统下播放时弹出“`EBADF: bad file descriptor, write`”问题如何解决？

![Windows 系统下播放时的 UNM 弹窗](https://user-images.githubusercontent.com/96377681/147851950-52d774ce-58b9-450a-b3f2-acc6e895d7dc.png)

升级到 [YesPlayMusic 0.4.5](https://github.com/qier222/YesPlayMusic/releases/tag/v0.4.5) 即可。0.4.5 版本解决了这个问题。

## 为什么首页的 Apple Music 歌单不会自动换新？

v1 的 Apple Music 歌单是写死的，纯粹是为了增加 YesPlayMusic 首页歌单的美感。

## 没有想提出的问题？

欢迎 [开 issue](https://github.com/qier222/YesPlayMusic/issues/new/choose)、在 [discussions](https://github.com/qier222/YesPlayMusic/discussions) 提出，或者是到 [Telegram 群组](https://t.me/yesplaymusic) 询问，开发者将尽量为您解决。