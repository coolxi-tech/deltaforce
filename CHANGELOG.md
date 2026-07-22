# 更新日志

本项目的主要变更都会记录在此文件中，版本记录参考 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/) 格式。

## [Unreleased]

### 性能优化

- 将 `Game::record()` 的 10 个独立上游请求改为批量并发执行，最大并发数为 5。
- 将 `Game::player()` 的角色资料和三类货币请求改为并行执行。
- 将 `/game/price` 在 `recent=1` 时的历史价格请求改为批量并发执行。
- 为 `/game/config` 和 `/game/items` 增加 300 秒缓存，减少重复访问上游接口。
- 为 `Tools` 控制器使用的物品集合增加 3600 秒缓存，降低初始化开销。

### 稳定性

- 为 Guzzle HTTP 客户端增加 3 秒连接超时和 12 秒请求超时，避免上游异常导致请求长期占用。
- 批量请求统一收集失败结果，并在任一上游请求失败时抛出异常，避免返回不完整数据。

### 部署

- Docker 镜像增加 cURL、SQLite PDO 和 OPcache 扩展。
- 为 CLI 模式启用并配置 OPcache。
- 清理 APT 软件包索引，减小最终镜像体积。

## [1.5.7] - 2026-04-26

### 新增

- 添加弹药配置文件。

### 改进

- 优化武器和弹药配置数据处理逻辑。
- 更新项目版本号至 `1.5.7`。

## [1.5.6] - 2026-04-26

### 新增

- 军需处接口增加集市商品数据。

## [1.5.5] - 2026-04-26

### 新增

- 添加军需处接口。

### 修复

- 修复 QQ 登录相关问题。
- 移除 QQ 登录调试信息。

## [1.5.4] - 2026-04-17

### 修复

- 修复 QQ 鉴权缺少 `getQrSig` 方法的问题。

[Unreleased]: https://github.com/WangBen137/deltaforce-data-api/compare/v1.5.7...HEAD
[1.5.7]: https://github.com/WangBen137/deltaforce-data-api/compare/v1.5.6...v1.5.7
[1.5.6]: https://github.com/WangBen137/deltaforce-data-api/compare/v1.5.5...v1.5.6
[1.5.5]: https://github.com/WangBen137/deltaforce-data-api/compare/v1.5.4...v1.5.5
[1.5.4]: https://github.com/WangBen137/deltaforce-data-api/releases/tag/v1.5.4
