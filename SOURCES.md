# 第三方源码获取指引

本文件对应 LofiDesk 1.0.0（2026-11-17 分发）的独立第三方组件。LofiDesk 应用主体为闭源软件；这里提供第三方组件依法保留的源码获取途径，不将这些组件改为闭源，也不包含主体的私有源码。

## yt-dlp 2026.08.19

本安装包内置该版本的独立 macOS Universal 可执行工具，保留其上游功能，仅采用应用分发所需的本地代码签名。

- [官方固定版本发行页](https://github.com/yt-dlp/yt-dlp/releases/tag/2026.08.19)
- [官方 yt-dlp 源码发布归档](https://github.com/yt-dlp/yt-dlp/releases/download/2026.08.19/yt-dlp.tar.gz)，6,020,567 字节，SHA-256：`072aad4f2a7604e92155f61a275a4752dc64046c8f6d90df3710525d94cd37c1`。
- [包含构建目录与工作流的完整标签源码归档](https://github.com/yt-dlp/yt-dlp/archive/refs/tags/2026.08.19.tar.gz)。
- [macOS 发行构建工作流](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/.github/workflows/build.yml#L286-L364)。
- [PyInstaller 打包脚本](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/bundle/pyinstaller.py)，包含 Universal 构建入口与许可文件打包方式。
- [macOS 固定依赖及哈希](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/bundle/requirements/macos.txt)、[curl_cffi/cffi 固定依赖及哈希](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/bundle/requirements/macos-curl_cffi.txt)、[项目构建配置](https://github.com/yt-dlp/yt-dlp/blob/2026.08.19/pyproject.toml)。

**yt-dlp 的主项目源码归档并不等于整个 PyInstaller 组合可执行文件的全部对应源码。** 后者还涉及随包 Python、Python 包、原生库及其构建材料。下面列出固定版本依赖和各自源码来源，应结合完整标签源码中的构建脚本使用。

## Python 包依赖与打包工具

版本依据为上述 yt-dlp 固定标签的 macOS 构建清单；带有操作系统或 Python 版本条件的项目应按对应清单判断。`curl_cffi 0.16.0` 与 `websockets 17.0.1` 另由本次随包工具内嵌 metadata 确认。PyInstaller、hooks、altgraph、macholib 为打包链来源，不意味着其全部开发工具都在最终包中运行。

以下均为相应版本在项目 PyPI 发布渠道上的源码包，SHA-256 来自该版本公开发布元数据。所有链接可直接下载，不要求获取或查看 LofiDesk 主体源码。

| 项目 | 版本 | 下载 | SHA-256 |
|---|---|---|---|
| mutagen | 1.48.1 | [源码归档](https://files.pythonhosted.org/packages/df/70/1675da133ea92227da41bf5b24e1c66be597ff736a1533ade41da986852f/mutagen-1.48.1.tar.gz) | `8f95637ab9f6f305cec6bd1294e197debe207998e3e068596563c74f86b0a173` |
| brotli | 1.2.0 | [源码归档](https://files.pythonhosted.org/packages/f7/16/c92ca344d646e71a43b8bb353f0a6490d7f6e06210f8554c8f874e454285/brotli-1.2.0.tar.gz) | `e310f77e41941c13340a95976fe66a8a95b01e783d430eeaf7a2f87e0a57dd0a` |
| certifi | 2026.7.22 | [源码归档](https://files.pythonhosted.org/packages/a3/c2/24167ea9858356b47a87a50d39908bfdb72ceeefe0041586e704e5376b3a/certifi-2026.7.22.tar.gz) | `741e2c3b351ddf169a738da9f2c048608ff7f2c5cc02f1ebc6b118bb090d5d55` |
| charset-normalizer | 3.5.0 | [源码归档](https://files.pythonhosted.org/packages/cb/31/4971872b3ed8715346231fb6eb4da8fcba65a4143c189db151ee28a2812b/charset_normalizer-3.5.0.tar.gz) | `49bd5feb59b0bf3cbf6ebcf4352e371c95b9da9bacd4449f8b64d0ad2c10a26e` |
| idna | 3.18 | [源码归档](https://files.pythonhosted.org/packages/cd/63/9496c57188a2ee585e0f1db071d75089a11e98aa86eb99d9d7618fc1edce/idna-3.18.tar.gz) | `ffb385a7e039654cef1ab9ef32c6fafe283c0c0467bba1d9029738ce4a14a848` |
| pycryptodomex | 3.23.0 | [源码归档](https://files.pythonhosted.org/packages/c9/85/e24bf90972a30b0fcd16c73009add1d7d7cd9140c2498a68252028899e41/pycryptodomex-3.23.0.tar.gz) | `71909758f010c82bc99b0abf4ea12012c98962fbf0583c2164f8b84533c2e4da` |
| requests | 2.34.2 | [源码归档](https://files.pythonhosted.org/packages/ac/c3/e2a2b89f2d3e2179abd6d00ebd70bff6273f37fb3e0cc209f48b39d00cbf/requests-2.34.2.tar.gz) | `f288924cae4e29463698d6d60bc6a4da69c89185ad1e0bcc4104f584e960b9ed` |
| urllib3 | 2.7.0 | [源码归档](https://files.pythonhosted.org/packages/53/0c/06f8b233b8fd13b9e5ee11424ef85419ba0d8ba0b3138bf360be2ff56953/urllib3-2.7.0.tar.gz) | `231e0ec3b63ceb14667c67be60f2f2c40a518cb38b03af60abc813da26505f4c` |
| websockets | 17.0.1 | [源码归档](https://files.pythonhosted.org/packages/f7/96/e01084f83a64bcb3a27994bd0cb0db68ff29d9c6707fae37ec19b18ba990/websockets-17.0.1.tar.gz) | `5baa9bc0dfbae8c507e51c8cf1b6d4628086f7a87bbd3a9952bd5f035451f1cc` |
| cffi | 2.1.1 | [源码归档](https://files.pythonhosted.org/packages/9e/ef/008a1939e372c06329a3fce4279c02f328488f3526744906eeec3da7ad5f/cffi-2.1.1.tar.gz) | `dd31f52ea1086513bb9df30f8fcee9b8918323ae067a3d5b78bc826a000712be` |
| curl-cffi | 0.16.0 | [源码归档](https://files.pythonhosted.org/packages/b4/23/d32e113b16dbfb458bea408871ed98dd12f306a366a04215e84537e0af7e/curl_cffi-0.16.0.tar.gz) | `b00b423da8028eb6221e3b63bcd63d681150c07cee8b16000d1f7ea292731895` |
| yt-dlp-ejs | 0.8.0 | [源码归档](https://files.pythonhosted.org/packages/d3/e6/cceb9530e8f4e5940f6f7822d90e9d94f1b85343329a16baaf47bbbb3de1/yt_dlp_ejs-0.8.0.tar.gz) | `d5fa1639f63b5c4af8d932495f60689d5370f1a095782c944f7f62a303eb104e` |
| pyinstaller | 6.22.0 | [源码归档](https://files.pythonhosted.org/packages/05/03/669d06735cf57d7e2e5dfc3c2e1643554b34c559eff21449c58172ca0335/pyinstaller-6.22.0.tar.gz) | `8b0166fff4583b374bbe7fa044bf03ddc33cab0f792a665807d96048e63f060e` |
| pyinstaller-hooks-contrib | 2026.6 | [源码归档](https://files.pythonhosted.org/packages/94/5b/c9fe0db5e83ee1c39b2258fa21d23b15e1a60786b6c5990ee5074ead8bb6/pyinstaller_hooks_contrib-2026.6.tar.gz) | `bef5002c32f4f50bd55b005da12cff64eca8783e7eaf86a06a62410164bab725` |
| altgraph | 0.17.5 | [源码归档](https://files.pythonhosted.org/packages/7e/f8/97fdf103f38fed6792a1601dbc16cc8aac56e7459a9fff08c812d8ae177a/altgraph-0.17.5.tar.gz) | `c87b395dd12fabde9c99573a9749d67da8d29ef9de0125c7f536699b4a9bc9e7` |
| macholib | 1.16.4 | [源码归档](https://files.pythonhosted.org/packages/10/2f/97589876ea967487978071c9042518d28b958d87b17dceb7cdc1d881f963/macholib-1.16.4.tar.gz) | `f408c93ab2e995cd2c46e34fe328b130404be143469e41bc366c807448979362` |

其中 Mutagen 的上游许可为 GPL-2.0-or-later；组合可执行文件的 GPLv3+ 声明由 yt-dlp 上游明确给出。[Mutagen 固定版本项目页](https://pypi.org/project/mutagen/1.48.1/)、[上游源码仓库](https://github.com/quodlibet/mutagen)。

## Python 与原生库

本次可执行文件中的 Python framework 元数据为 **CPython 3.14.6**。

- [CPython 3.14.6 官方源码树](https://github.com/python/cpython/tree/v3.14.6)与[固定标签源码归档](https://github.com/python/cpython/archive/refs/tags/v3.14.6.tar.gz)。
- [该版本 macOS installer 构建脚本](https://github.com/python/cpython/blob/v3.14.6/Mac/BuildScript/build-installer.py)提供 Python macOS 构建及其外部库获取材料。
- [curl_cffi 0.16.0 源码](https://github.com/lexiforest/curl_cffi/tree/v0.16.0)与其构建说明提供所用 curl-impersonate/原生库的来源及构建方式。对应项目的源码获取不能由仅下载 Python wrapper 的源码包来替代。
- [OpenSSL 源码与版本获取入口](https://github.com/openssl/openssl)、[Zstandard 源码与版本获取入口](https://github.com/facebook/zstd)等项目亦在上游第三方许可汇编中列出。

原生库的确切补丁版本应以相应 Python/curl_cffi 发行构建材料为准，不从 LofiDesk 自身版本号推断。本索引未声称所有第三方项目都经本次独立重新编译，也未将通用项目首页称作某个未知补丁版本的完整对应源码。

## QuickJS-NG 与 EJS

QuickJS-NG 使用 **v0.17.0** 官方源码，构建目标为 `arm64;x86_64`、最低 macOS `13.0`；本分发未修改引擎源码。

- [QuickJS-NG 固定标签源码归档](https://github.com/quickjs-ng/quickjs/archive/refs/tags/v0.17.0.tar.gz)；对应 codeload 归档 SHA-256 为 `559bc4c420475e55c7ab4510adbc562f55d7524d75e8e89d79ce4bb02f5687d9`。
- [同版本 CMake 构建文件](https://github.com/quickjs-ng/quickjs/blob/v0.17.0/CMakeLists.txt)。使用 Release 构建、`CMAKE_OSX_ARCHITECTURES=arm64;x86_64`、`CMAKE_OSX_DEPLOYMENT_TARGET=13.0`，目标 `qjs_exe`。
- [yt-dlp-ejs 0.8.0 完整标签源码](https://github.com/yt-dlp/ejs/tree/0.8.0)与[标签源码归档](https://github.com/yt-dlp/ejs/archive/refs/tags/0.8.0.tar.gz)，包含 JS 源码和构建材料；其 PyPI 源码包另见上表。

## 下载与持续可用性

[GPLv3 第 6(d) 节](licenses/GPL-3.0.txt)允许网络发行时通过不同服务器提供对应源码，但必须在二进制下载旁清楚说明获取位置，并保持等效、无额外收费的源码访问。使用第三方托管并不会取消分发方持续确保可用的责任。

因此，每个安装包的 Release 页面应同时链接本文件及 [第三方许可说明](THIRD_PARTY_NOTICES.md)。如果某个固定版本链接失效，请在本项目 Issues 报告对应组件、版本和失效链接；不要提交 Cookie、登录信息或签名播放地址。维护者应恢复相应源码访问，而非仅用“上游提供”代替失效资源。

## 本发行页保留的第三方源码镜像

以下附件仅属于独立开源组件，不包含 LofiDesk 主体源码。其余固定版本来源与构建材料见上文。

- [third-party-mutagen-1.48.1-source.tar.gz](https://github.com/Michael-IT001/LofiDesk/releases/download/v1.0.0/third-party-mutagen-1.48.1-source.tar.gz)，SHA-256：`8f95637ab9f6f305cec6bd1294e197debe207998e3e068596563c74f86b0a173`。
- [third-party-pyinstaller-6.22.0-source.tar.gz](https://github.com/Michael-IT001/LofiDesk/releases/download/v1.0.0/third-party-pyinstaller-6.22.0-source.tar.gz)，SHA-256：`8b0166fff4583b374bbe7fa044bf03ddc33cab0f792a665807d96048e63f060e`。
- [third-party-yt-dlp-2026.08.19-source.tar.gz](https://github.com/Michael-IT001/LofiDesk/releases/download/v1.0.0/third-party-yt-dlp-2026.08.19-source.tar.gz)，SHA-256：`072aad4f2a7604e92155f61a275a4752dc64046c8f6d90df3710525d94cd37c1`。
- [third-party-yt_dlp_ejs-0.8.0-source.tar.gz](https://github.com/Michael-IT001/LofiDesk/releases/download/v1.0.0/third-party-yt_dlp_ejs-0.8.0-source.tar.gz)，SHA-256：`d5fa1639f63b5c4af8d932495f60689d5370f1a095782c944f7f62a303eb104e`。
