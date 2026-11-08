# ClassiCube 单文件网页版

一个方块沙盒游戏，整个游戏（引擎、世界生成、贴图）都打包进 **一个 HTML 文件**，双击即可在浏览器里离线运行，不需要安装、不需要联网、不需要服务器。

在线试玩：<https://terry65536.github.io/classicube-html/>（页面本身需要联网加载，加载完成后游戏完全在本地运行）

- 版本：ClassiCube 1.3.9
- 文件：`ClassiCube.html`（约 790 KB）
- 浏览器：Edge / Chrome 桌面版，建议开启硬件加速
- 打包与网页适配：terry65536

## 开始游戏

1. 双击 `ClassiCube.html`，用 Edge 或 Chrome 打开。
2. 游戏会直接生成一个随机世界并进入第一人称模式。
3. 按 `F11` 全屏，体验更好。

在触屏设备（Windows 平板、二合一笔记本的触摸模式）上，游戏会自动切换为触屏布局：左下角是方向键，右下角是跳跃键，右上角是飞行/速度，顶部中间的 `…` 打开暂停菜单。

## 操作

| 操作 | 桌面 | 触屏 |
| --- | --- | --- |
| 移动 | `W` `A` `S` `D` | 左下方向键拖动 |
| 跳跃 | `空格` | 右下跳跃键 |
| 视角 | 移动鼠标 | 在画面上滑动 |
| 挖掘 | 鼠标左键 | 长按方块 |
| 放置 | 鼠标右键 | 点击方块 |
| 切换方块 | 滚轮 / `1`–`9` | 点击底部物品栏 |
| 暂停菜单 | `Esc` | 顶部 `…` 按钮 |

完整键位可以在暂停菜单 → `Controls` 里查看和修改。

## 关于这个版本

在原版 ClassiCube Web 客户端的基础上做了以下改动：

- 构建为单文件版本：WebAssembly、游戏逻辑与贴图全部内联进 HTML。
- 支持 `file://` 直接打开：原版 Web 客户端需要 HTTP 服务器并依赖 IndexedDB，此版本改为内存文件系统启动。
- 增加触屏检测：Windows 平板不再被当作纯桌面设备，会自动显示触屏按钮。
- 中文加载界面与全屏画布适配。

默认玩家名为 `Player`。用文本编辑器打开 HTML，搜索 `arguments: ['Player']` 即可改成别的名字。

## 已知限制

- 从 `file://` 打开时浏览器会禁用 IndexedDB，因此**设置和存档不会跨会话保留**，每次打开都会重新生成世界。把文件放到 HTTP 服务器上访问时可以正常保存。
- 玩家皮肤会尝试从 `cdn.classicube.net` 加载；离线时使用内置默认皮肤，不影响游戏。
- 未包含音效与音乐。
- 联机功能未在此版本中验证。

## 版权与致谢

本文件包含的开源组件：

- **ClassiCube 1.3.9** — 游戏引擎、世界生成、渲染与网络代码，Copyright (c) 2014–2024, UnknownShadow200 及贡献者。BSD 3-Clause。原项目：<https://github.com/ClassiCube/ClassiCube>
- **网页版贴图包** — 取自 ClassiCube 仓库的 `misc/cc_textures.zip`，网页客户端贴图与图标由 **Goodlyay** 设计。
- **Emscripten 运行时** — Copyright (c) 2010–2014, Emscripten authors，MIT / University of Illinois/NCSA 双许可。
- **musl libc** — Copyright © 2005–2020, Rich Felker 等，MIT 许可。

FreeType、BearSSL、tinyalloc 等组件存在于上游源码树中，但网页版没有编译它们，因此不包含在本文件里。

详细的组件清单、作者对照、许可证文本以及本版本的逐文件修改记录，见同目录下的 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。许可证全文见 `LICENSE-ClassiCube.txt`、`LICENSE-Emscripten.txt`、`LICENSE-musl.txt`，上游致谢名单见 `CONTRIBUTORS-ClassiCube.txt`。

游戏加载界面会显示一行简短的版权信息。本版本的网页适配与打包由 **terry65536** 完成；ClassiCube 名称及贡献者名称仅用于说明来源，不代表其对本版本的认可或背书。
