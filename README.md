# RustMusic-Linux

本仓库是 [RustMusic](https://github.com/LingyunStudio/RustMusic) 的 Linux 版。

## 改动

在上游 Windows 版的基础上补齐了 Linux 的构建与运行：

- Windows 专属依赖（`wasapi`、`windows` 等）移入 `cfg(windows)`，`keyring` 分平台后端（Windows 用凭据管理器，Linux 用 Secret Service）。
- WASAPI 独占、WebView2 挂起、更新器静默安装、DWM 窗口圆角等 Windows 专属功能在 Linux 下 `cfg` 门控、优雅降级（如独占模式回退共享播放、相关设置项自动隐藏）。
- 打开链接 / 文件夹改用 `xdg-open`，系统媒体控制走 MPRIS，修正 `db.rs` 路径分隔符导致 Linux 下删除媒体库文件夹不生效的问题。
- `linux/` 提供 `PKGBUILD` 与 `.desktop`，可在 Arch / CachyOS 用 `makepkg -si` 构建安装。

## 许可证

基于 [Apache-2.0](LICENSE) 发布。其中 `src-tauri/src/qrc.rs` 来自 [navidrome-lyrics-plugin](https://github.com/J0R6IT0/navidrome-lyrics-plugin)（MIT），按 Apache-2.0 修改后并入，文件头部保留原始版权声明。
