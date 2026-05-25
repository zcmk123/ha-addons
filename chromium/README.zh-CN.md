# Chromium（Home Assistant 加载项）

[English](./README.md)

通过 Web 图形界面使用 Chromium 浏览器（支持 Ingress）。本加载项基于 `jlesage/chromium` 容器镜像。

## 使用方法

- 在 Home Assistant 左侧边栏打开该加载项的面板即可使用。
- 推荐使用 Ingress 访问（一般不需要手动映射端口）。

## 端口说明

- `5800/tcp`：Web 界面（使用 Ingress 时不需要暴露）
- `5900/tcp`：VNC（可选，使用 Ingress 时不需要暴露）

## 持久化存储

- 容器使用 `/config` 保存配置、状态、日志等数据。
- 你在浏览器里下载的文件通常会落到容器的 `/config` 或你在 Chromium 内配置的路径；如果需要和 HA 主机共享文件，建议结合 `/share` 等映射目录在应用内选择保存位置。

## 配置项

本加载项将 `jlesage/chromium` 的常用环境变量以加载项配置的形式提供。

常用配置示例：

- `LANG`、`TZ`：语言/时区。
- `DISPLAY_WIDTH`、`DISPLAY_HEIGHT`：默认窗口大小。
- `WEB_AUDIO`：启用网页界面音频。
- `WEB_FILE_MANAGER`、`WEB_TERMINAL`：启用网页文件管理器/终端。
- `WEB_AUTHENTICATION`：为网页界面启用登录保护（需要 HTTPS）。
- `SECURE_CONNECTION`：启用 HTTPS 与加密 VNC。
- `VNC_PASSWORD`：设置 VNC 密码。
- `CHROMIUM_APP_URL`：以“应用模式”启动指定 URL（更像一个固定网页应用）。

## 注意事项

- 如果需要在非可信网络环境访问，请务必开启 HTTPS/认证等安全选项。
