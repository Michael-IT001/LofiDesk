# 第三方组件声明

LofiDesk 的应用主体为闭源软件，主体源代码不在本仓库公开。随安装包提供的独立工具、运行时、辅助脚本及第三方资源，不会因为这一说明而改变各自的许可证或权利归属。LofiDesk 的闭源声明不限制用户依据第三方许可证已享有的权利。

## 随包组件

| 组件 | 版本 | 许可与说明 |
|---|---|---|
| yt-dlp 独立 macOS 可执行工具 | 2026.08.19 | yt-dlp 自身源代码为 Unlicense；上游说明其 PyInstaller 发行物包含其他项目代码，组合可执行文件按 GPLv3+ 分发。不能把这个二进制仅标成 Unlicense。 |
| QuickJS-NG | 0.17.0 | MIT。以同版本官方源码重建 Universal 可执行文件，部署目标 macOS 13.0，未改动引擎源码。 |
| yt-dlp-ejs | 0.8.0 | `Unlicense AND MIT AND ISC`；含 Meriyah 与 Astring 等上游许可头。 |
| Python 与 yt-dlp 打包的其他运行时/库 | 见上游固定版本构建清单 | 保留各自许可。上游完整许可汇编含不同操作系统的组件，并非其中每一项都存在于 macOS 包。 |

yt-dlp 在本应用中作为独立子进程调用；本仓库没有把 LofiDesk 主体源代码以 GPL、MIT 或其他开源许可证发布。内置可执行文件可能由分发方附加本地 ad-hoc 签名；该操作不表示修改第三方程序的业务源码。

安装包包含可读的 `YouTubeSession.py` 会话辅助脚本与开源的 EJS 资源。这是软件运行所需的分发内容；“主体闭源”不等于安装包中的每一份文件都不可阅读。

## 许可全文

- [yt-dlp 2026.08.19 上游完整第三方许可汇编](licenses/yt-dlp-2026.08.19-THIRD_PARTY_LICENSES.txt)
- [GNU GPL 第 3 版全文](licenses/GPL-3.0.txt)
- [QuickJS-NG 0.17.0 MIT 许可](licenses/quickjs-ng-0.17.0-MIT.txt)
- [yt-dlp-ejs 0.8.0 及其所含组件声明](licenses/yt-dlp-ejs-0.8.0-LICENSES.txt)

上述 yt-dlp 许可汇编与本次随包可执行文件中的同名内嵌文件一致，SHA-256 为 `472aefe951c7db35e1657c1d13fd337140511ed6f2b329205105ad441c5a02b7`。上游原件见 [固定版本文件](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/THIRD_PARTY_LICENSES.txt)。

## 第三方源码获取

对应版本源码、构建脚本和依赖获取入口见 [SOURCES.md](SOURCES.md)。这些链接涉及独立第三方组件，不包含 LofiDesk 主体的私有源码。下载页应在安装包旁提供本说明和源码获取指引，用户无需购买或另付费用才能获取这些公开来源。

## 内容与标识

YouTube、Lofi Girl、Claude FM 等名称、标识、频道及媒体内容属于各自权利人。LofiDesk 为独立第三方软件，这里不表示相关平台、频道或品牌的官方合作或背书。直播内容的可用性和使用规则由其提供方决定。
