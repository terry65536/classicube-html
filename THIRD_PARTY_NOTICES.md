# 第三方组件、作者与许可证

本文件列出 `ClassiCube.html` 中实际包含的代码、素材及其作者和许可证，以及本版本（terry65536 打包）做了哪些修改。

## 一、包含在 HTML 中的组件

| 组件 | 作者 / 版权方 | 许可证 | 在本文件中的形式 |
| --- | --- | --- | --- |
| ClassiCube 1.3.9（游戏引擎、世界生成、渲染、网络协议） | Copyright (c) 2014–2024, UnknownShadow200 及贡献者 | BSD 3-Clause | WebAssembly + 随附 JavaScript |
| ClassiCube 网页版贴图（terrain、gui、touch、实体皮肤等） | 贴图与图标由 **Goodlyay** 为 ClassiCube 网页客户端设计 | 随 ClassiCube 项目仓库分发 | Base64 内联进 HTML |
| Emscripten 运行时（JS 加载器、WebAssembly 支持代码） | Copyright (c) 2010–2014, Emscripten authors | MIT 或 University of Illinois/NCSA（双许可） | 编译进游戏 JS |
| musl libc（Emscripten 使用的 C 标准库） | Copyright © 2005–2020, Rich Felker 等 | MIT | 编译进 WebAssembly |

完整许可证文本随文件提供：

- `LICENSE-ClassiCube.txt` — ClassiCube，BSD 3-Clause
- `LICENSE-Emscripten.txt` — Emscripten，MIT + UIUC/NCSA
- `LICENSE-musl.txt` — musl，MIT
- `CONTRIBUTORS-ClassiCube.txt` — 上游项目致谢名单

## 二、源码树中存在、但**未包含**在本文件中的组件

这些组件属于 ClassiCube 的其他平台构建，网页版编译时已被关闭或未参与链接，因此不在 `ClassiCube.html` 里：

| 组件 | 作者 | 许可证 | 未包含的原因 |
| --- | --- | --- | --- |
| FreeType（精简版） | Copyright 1996–2018, David Turner, Robert Wilhelm, Werner Lemberg | FreeType License / GPLv2 | 网页版使用浏览器 Canvas 2D 绘制文字，编译时 `CC_BUILD_FREETYPE` 被关闭 |
| BearSSL | Copyright (c) 2016, Thomas Pornin | MIT | 网页版通过浏览器 `fetch` 联网，未启用 BearSSL 后端 |
| fix16_sqrt | Copyright (c) 2019, Christophe Meessen | MIT | 仅 32X / Saturn / GBA / PS1 平台使用 |
| tinyalloc | 见 `third_party/tinyalloc` | MIT | 仅部分低内存平台使用 |

## 三、本版本的修改（作者：terry65536）

对上游源码的修改仍按 **BSD 3-Clause** 分发；新增的 HTML 外壳与打包脚本由 terry65536 编写，按 **MIT** 分发。

| 文件 | 原作者 | 修改者 | 修改内容 |
| --- | --- | --- | --- |
| `src/webclient/interop_web.js` | UnknownShadow200 | terry65536 | 从内联 Base64 还原贴图包并写入 CCFS；`file://` 下跳过会挂起的 IndexedDB 加载（含超时与防重入）；新增触屏设备检测 `interop_IsTouchDevice` |
| `src/webclient/Window_Web.c` | UnknownShadow200 | terry65536 | 将触屏检测并入原版 `is_ios || droid` 判断，使 Windows 平板启用触屏 UI |
| `web/index.template.html` | —（新增） | terry65536 | 加载界面、版权行、画布 DPR 自适应、默认用户名、`#diag` 诊断模式 |
| `build_web.sh` | —（新增） | terry65536 | 直接调用 emcc 的构建脚本，`-sSINGLE_FILE=1` 将 wasm 内联 |
| `package_html.py` | —（新增） | terry65536 | 将游戏 JS 与 Base64 贴图包拼装为单个 HTML |
| `assets/texpack.zip` | Goodlyay / ClassiCube | 原样复制 | 取自上游 `misc/cc_textures.zip`，未修改内容 |

没有修改的部分：C 引擎、渲染器、世界生成、方块定义、存档格式、网络协议、原版键位与玩法。WebAssembly 中的游戏本体是上游 ClassiCube 1.3.9 的原样编译结果。

## 四、说明

- 本版本不包含任何 Mojang / Minecraft 的代码、贴图或音频。
- 不包含音乐与音效；网页版音效默认音量为 0。
- 玩家皮肤会尝试从 `cdn.classicube.net` 加载；离线时使用内置默认皮肤。
- ClassiCube 的名称与贡献者名称仅用于说明来源，不表示其对本文档所述版本提供认可或背书（BSD 3-Clause 第 3 条）。
