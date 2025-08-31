# 项目概述

这是一个基于 Dart 和 Flutter 的 monorepo 项目，旨在提供一个聚合直播解决方案。项目包含四个主要部分：

*   **`simple_live_app`**: 一个功能丰富的 Flutter 应用程序，面向普通用户，提供多平台（Android, iOS, Windows, macOS, Linux）的直播观看体验。
*   **`simple_live_console`**: 一个 Dart 命令行工具，用于获取直播间信息、播放链接和实时弹幕。
*   **`simple_live_core`**: 一个 Dart 核心库，封装了与多个直播平台（Bilibili, 虎牙, 斗鱼, 抖音）交互的逻辑，提供统一的直播数据接口。
*   **`simple_live_tv_app`**: 一个专为电视平台设计的 Flutter 应用程序，优化了电视端的用户体验，强制横屏和全屏显示。

**主要技术栈：**

*   **Dart**: 主要编程语言。
*   **Flutter**: 用于构建 `simple_live_app` 和 `simple_live_tv_app` 的 UI 框架。
*   **GetX**: Flutter 应用程序的状态管理、依赖注入和路由管理。
*   **Hive**: 快速的本地 NoSQL 数据库，用于数据持久化。
*   **MediaKit**: 跨平台视频播放库。
*   **Dio**: 强大的 HTTP 客户端，用于网络请求。
*   **WebSocketChannel**: WebSocket 客户端，用于实时弹幕等功能。
*   **Protobuf**: 数据序列化协议。

# 构建和运行

## 1. 获取依赖

在项目根目录运行以下命令，为所有子项目获取依赖：

```bash
flutter pub get
```

## 2. 运行应用程序

### `simple_live_app` (Flutter 应用)

在 `simple_live_app` 目录下运行：

```bash
flutter run
```

### `simple_live_console` (Dart 命令行工具)

在项目根目录或 `simple_live_console` 目录下运行：

```bash
dart run simple_live_console:simple_live_console -i [直播间URL]
dart run simple_live_console:simple_live_console -d [直播间URL]
```

例如：

```bash
dart run simple_live_console:simple_live_console -i https://live.bilibili.com/12345
dart run simple_live_console:simple_live_console -d https://live.douyu.com/67890
```

### `simple_live_tv_app` (Flutter TV 应用)

在 `simple_live_tv_app` 目录下运行：

```bash
flutter run
```

## 3. 构建应用程序

### `simple_live_app` 和 `simple_live_tv_app`

在各自的子项目目录下运行，例如构建 Android APK：

```bash
flutter build apk
```

构建其他平台（如 Windows, macOS, Linux）请参考 Flutter 官方文档。

## 4. 运行测试

### 所有子项目

在各自的子项目目录下运行：

```bash
flutter test # 对于 Flutter 应用
dart test # 对于 Dart 包和命令行工具
```

# 开发约定

*   **代码风格**: 项目遵循 Dart 和 Flutter 的推荐代码风格，并通过 `analysis_options.yaml` 文件进行 Linting 检查。
*   **测试**: 每个子项目都包含 `test` 目录，鼓励编写单元测试和 Widget 测试以确保代码质量。
*   **模块化**: 项目采用模块化设计，核心逻辑集中在 `simple_live_core` 中，各应用程序通过依赖该核心库实现功能。
