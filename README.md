# 缠命沈宅 — Web 版

这是把原本依赖 Windows + Edge + Python 的 LockScreen 改成纯静态 Website 版本。

## 支持
- Android Chrome / Edge
- iPhone Safari / Chrome
- Windows / macOS / Linux 浏览器
- 不需要 Google Play Services for AR
- 不需要 Python、Edge Kiosk 或 EXE
- `assets/jumpscare.mp4` 已包含

## Jumpscare 音频逻辑
- 0–5 秒：视频播放，但保持静音
- 第 5 秒开始：网页视频的 `volume = 1`，并解除 `muted`
- 视频结束后进入假桌面

### 重要限制
普通 Website **不能强制把 Android/iPhone 的系统音量调到最大**，也不能阻止玩家按手机实体音量键降低系统音量。这是浏览器/操作系统的安全限制。

代码能强制控制的是网页 `<video>` 自身的媒体音量为 100%。如果玩家的系统音量本身很低，网页无法把它直接改成系统最大音量。

## 关于截图里的 AR 错误
截图中的：
`Google Play Services for AR required`

这是 Android 的 ARCore / Google Play Services for AR 依赖问题，不是普通 HTML/CSS/JavaScript 本身的问题。

如果你的目标只是这个锁屏 + jumpscare 效果，Web 版已经完全移除 AR 依赖，因此 Android、iPhone 和电脑浏览器都不需要 Google Play Services for AR。

如果你以后真的需要“摄像头 + AR 物体”的功能，则需要另外做跨平台 WebAR；Google Play Services for AR 本身不能作为 iPhone 的跨平台方案。

## 部署
把整个文件夹上传到任何支持静态网站的 Hosting，并确保：
- `index.html` 在网站根目录
- `assets/bg.jpg`
- `assets/desktop.jpg`
- `assets/jumpscare.mp4`

不要只上传 `index.html`，否则视频和背景图片会找不到。

建议使用 HTTPS 网站，因为手机浏览器对媒体播放、全屏等能力在 HTTPS 下兼容性更好。
