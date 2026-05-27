# Guga Eye Rest Pet

Guga Eye Rest Pet 是一个 Windows 优先的 Electron 桌面护眼提醒应用。它会在桌面上显示可爱的咕嘎桌宠，在设定时间提醒你休息眼睛，并用全屏半透明倒计时遮罩陪你完成一次短暂休息。

![Guga desktop pet](docs/screenshots/pet-window.png)

## 产品截图

![Settings window](docs/screenshots/settings-window.png)

![Break overlay](docs/screenshots/break-overlay.png)

## 功能

- 桌面咕嘎窗口：无边框、透明背景、可拖拽、默认置顶、记住位置。
- 护眼提醒：到点弹出提醒窗口，可开始休息、稍后提醒或跳过一次。
- 全屏休息遮罩：半透明背景、居中倒计时、支持 Esc 或按钮提前结束。
- 设置持久化：提醒间隔、休息时长、遮罩主题、置顶、暂停提醒、开机自动启动。
- 托盘菜单：打开设置、立即休息、暂停/恢复提醒、退出。
- 多帧动画：idle、remind、resting、happy，以及保留的 idle 挥手待机动作。
- 轻量互动：投喂、心情状态、今日统计和成就徽章。

> 本项目刻意保持简单：不包含 Live2D、AI 聊天、Steam 集成或复杂动画系统。

## 安装包

在 Windows 上生成可安装程序：

```powershell
npm.cmd install
npm.cmd run dist
```

安装包会输出到：

```text
release/Guga Eye Rest Pet-Setup-0.1.0.exe
```

安装后可以在设置页开启 **Start with Windows**，应用会通过 Electron 登录项设置随 Windows 登录自动启动。

如果当前机器无法联网下载 electron-builder 的 NSIS 工具包，可以先生成离线可运行目录：

```powershell
npm.cmd run pack:dir
```

输出目录：

```text
release/win-unpacked/Guga Eye Rest Pet.exe
```

仓库也包含 GitHub Actions 工作流，推送到 `main` 后会在 Windows runner 上自动构建安装包，并上传为 workflow artifact。

## 开发运行

```powershell
npm.cmd install
npm.cmd run dev
```

常用检查：

```powershell
npm.cmd run typecheck
npm.cmd run build
npm.cmd run sprites
```

## 素材管线

将透明 PNG 帧图放入：

```text
src/assets/pet/frames/{state}/
```

然后运行：

```powershell
npm.cmd run sprites
```

脚本会生成：

```text
src/assets/pet/sprites/{state}.png
src/assets/pet/sprites/manifest.json
```

当前支持状态：

- `idle`
- `idle-scarf`
- `remind`
- `resting`
- `happy`

## 项目结构

```text
electron/
  main.ts
  services/
  windows/
src/
  App.tsx
  styles.css
  assets/pet/
docs/screenshots/
scripts/
```

## 默认设置

- 提醒间隔：120 分钟
- 休息时长：60 秒
- 稍后提醒：生产环境 10 分钟，开发环境 10 秒
- 默认置顶：开启
- 默认暂停提醒：关闭
- 默认开机启动：关闭

## 技术栈

- Electron
- React
- TypeScript
- Vite
- electron-store
- electron-builder

## License

MIT
