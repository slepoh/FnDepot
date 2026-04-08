# LX Music Sync Server (Enhanced Edition)

<div align="center">
  
---
本项目内置了一个功能强大的 **Web 播放器**，让你可以随时随地在浏览器中享受音乐。同时，它也是一个增强版的 LX Music 数据同步服务端。

## ✨ Web 播放器核心特性

### 1. 现代化界面

采用清爽的现代化 UI 设计，支持深色模式，提供极致的视觉体验。

### 2. 多源搜索

支持聚合搜索各大音乐平台的资源，想听什么搜什么。

### 3. 内容与播放列表

支持**多平台歌单**的浏览、搜索与一键播放，提供直观的**歌单详情**面板，包含封面、作者、简介等完整信息。**播放队列**支持拖拽排序、批量管理及快速定位当前播放。

### 4. 强大的播放控制

支持播放模式切换、音质选择、歌词显示、睡眠定时、播放倍数等功能。

### 5. 缓存管理

内置**全自动化缓存系统**，可自动保存歌词、链接及歌曲文件，通过专门的**缓存控制面板**实现颗粒化管理，极大提升弱网环境下的播放流畅度。

### 6. 歌词卡片分享

新增**歌词卡片分享**功能，支持自定义卡片比例（竖版/横版/方版）、色彩风格（深色/浅色/专辑色）及歌词行数，一键生成精美海报，支持旋转缩放。

### 7. 主题定制与系统功能

支持**多套现代化主题**（如森之韵、深海鲨、暖阳意、绯红月等），并可根据系统自动切换暗亮模式。系统设置支持**自动更新网络歌单**、**账号设置自动备份**及**多维度代理**配置，确保播放顺滑稳定。

### 8. 自定义源管理

支持导入自定义源脚本，扩展更多音乐来源。

## 🔒 访问控制与安全

为了保护你的隐私，Web 播放器支持开启访问密码。

### 开启方式

1. **环境变量配置**（推荐 Docker 用户使用）：
   - `ENABLE_WEBPLAYER_AUTH=true`: 开启认证
   - `WEBPLAYER_PASSWORD=yourpassword`: 设置访问密码
2. **Web 界面配置**：
   登录管理后台（默认端口 9527），进入 **"系统配置"**，勾选 **"启用 Web 播放器访问密码"** 并设置密码。

## 📱 移动端适配

Web 播放器针对移动端进行了深度优化，手机浏览器访问也能获得原生 App 般的体验。

---

### 访问说明

- **Web 播放器**: `http://your-ip:9527/music`
- **同步管理后台**: `http://your-ip:9527` (默认密码: `123456`)

---

## 🛠️ 配置说明

可以直接编辑 `config.js`。环境变量优先级最高：

| 环境变量                           | 对应配置项                       | 说明                                                            | 默认值             |
| ---------------------------------- | -------------------------------- | --------------------------------------------------------------- | ------------------ |
| `PORT`                           | `port`                         | 服务端口                                                        | `9527`           |
| `BIND_IP`                        | `bindIP`                       | 绑定 IP                                                         | `0.0.0.0`        |
| `FRONTEND_PASSWORD`              | `frontend.password`            | Web 管理界面访问密码                                            | `123456`         |
| `SERVER_NAME`                    | `serverName`                   | 同步服务名称                                                    | `My Sync Server` |
| `MAX_SNAPSHOT_NUM`               | `maxSnapshotNum`               | 保留的最大快照数量                                              | `10`             |
| `CONFIG_PATH`                    | -                              | 指定外部配置文件的绝对路径                                      | -                  |
| `DATA_PATH`                      | -                              | 指定数据存储目录的绝对路径                                      | `./data`           |
| `LOG_PATH`                       | -                              | 指定日志输出目录的绝对路径                                      | `./logs`           |
| `PROXY_HEADER`                   | `proxy.header`                 | 代理转发 IP 头 (如 `x-real-ip`)                               | -                  |
| `USER_ENABLE_ROOT`               | `user.enableRoot`              | 启用根路径 (开启后连接URL即为 `ip:port`，不允许不同用户密码相同) | `false`          |
| `USER_ENABLE_PATH`               | `user.enablePath`              | 启用用户路径 (开启后连接URL需为 `ip:port/用户名`，允许密码相同) | `true`           |
| `WEBDAV_URL`                     | `webdav.url`                   | WebDAV 地址                                                     | -                  |
| `WEBDAV_USERNAME`                | `webdav.username`              | WebDAV 用户名                                                   | -                  |
| `WEBDAV_PASSWORD`                | `webdav.password`              | WebDAV 密码                                                     | -                  |
| `SYNC_INTERVAL`                  | `sync.interval`                | WebDAV 自动备份间隔(分钟)                                       | `60`             |
| `ENABLE_WEBPLAYER_AUTH`          | `player.enableAuth`            | 是否启用 Web 播放器访问密码                                     | `false`          |
| `WEBPLAYER_PASSWORD`             | `player.password`              | Web 播放器访问密码                                              | 123456             |
| `DISABLE_TELEMETRY`              | `disableTelemetry`             | 是否禁用匿名数据统计，系统更新提示以及系统公告提示              | `false`          |
| `ENABLE_PUBLIC_USER_RESTRICTION` | `user.enablePublicRestriction` | 是否启用公开用户权限限制 (限制上传、删除公开源、缓存到服务器等) | `true`           |
| `LIST_ADD_MUSIC_LOCATION_TYPE`   | `list.addMusicLocationType`    | 添加歌曲到列表时的位置 (`top` / `bottom`)                       | `top`            |
| `PROXY_ALL_ENABLED`               | `proxy.all.enabled`             | 是否启用外发请求代理 (针对 Music SDK)                            | `false`          |
| `PROXY_ALL_ADDRESS`               | `proxy.all.address`             | 代理地址 (支持 http:// 或 socks5://)                           | -                  |
| `LX_USER_<用户名>`                 | `users` 数组                   | 快速添加用户，值为该用户的密码 (如 `LX_USER_test=123`)        | -                  |

> **提示**：目前服务支持 `启用根路径` (URL配置为 `ip:port`) 和 `启用用户路径` (URL配置为 `ip:port/username`) 两种数据同步连接方式。如果没有启用用户路径，则必须保证每一个同步用户的鉴权密码不重复。
