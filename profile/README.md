# 欢迎来到 Kuro-Bridge

**Kuro-Bridge** 是做 Minecraft 服务器与社交平台互通的研发组织。核心项目 **KuroAdapter** 是一个 Paper 服务端插件：丢进 `plugins/` 即可通过 WebSocket 与机器人框架通信，实现「游戏 ↔ 群聊」的双向消息互通。

> 本组织与任何机器人框架官方均无隶属关系，是独立的社区项目。

## 主要仓库

- **[Kuro-Bridge/KuroAdapter](https://github.com/Kuro-Bridge/KuroAdapter)** —— 互通插件（Java 薄壳 + Node 业务核心，单仓多包）

## 它是怎么工作的

```
Minecraft 服务端
  └─ KuroAdapter（Paper JAR）
       ├─ Java 薄壳：事件 / 命令 / 权限桥接
       └─ 内嵌 Node 子进程：业务核心 + WebSocket 服务端
            └─ 对端协议端主动连入
```

- 插件始终是 WS 服务端，对端主动连入；双方只认一套自研协议
- 内置与外部两种模式只差打包，业务核心完全一致
- Java 侧只做薄壳与进程管理，业务逻辑集中在 TypeScript 核心

## 工程约定

- 技术栈：TypeScript（Biome + 严格 tsconfig）与 Java 21 薄壳（Gradle 多模块）
- 协议以 zod schema 为唯一事实来源，禁止手写消息类型
- 架构与决策记录随仓库文档维护

## 交流与反馈

欢迎在仓库 Issue 中反馈问题或建议。

## 许可证

[MIT](https://github.com/Kuro-Bridge/KuroAdapter/blob/master/LICENSE)
