---
title: "Filesystem agent showcase"
description: "Projects that lean on the filesystem paradigm to organize agent context, skills, and backends."
source: "/showcase.md"
---

## OpenViking

- 字节跳动开源的一款 AI Agent 上下文管理系统：OpenViking。
- 核心创新是文件系统范式，将上下文当作文件统一管理，而非文本切片。
- 像管理本地文件一样组织 Agent 记忆、资源、技能，分层上下文按需加载降低 Token 消耗。
- 记忆可自迭代进化，检索过程可视化，包含目录浏览与文件选择轨迹。
- 标签：#OpenViking #aiagent记忆 #aiagent。

链接：https://github.com/volcengine/OpenViking

## AGFS (Agent FS)

- Aggregated File System — 一切皆文件，后端服务通过 RESTful 文件接口呈现。
- 为多代理协调提供统一接口：消息队列、数据库、对象存储、KV 等都映射为文件操作。
- 例子：
  - `redis.set("key", "value")` → `echo "value" > /kvfs/keys/mykey`
  - `sqs.send_message(queue, msg)` → `echo "msg" > /queuefs/q/enqueue`
  - `s3.put_object(bucket, key, data)` → `cp file /s3fs/bucket/key`
- 好处：LLM 原生理解文件操作；接口统一降低认知负担；可用管道与重定向实现可组合调试。

链接：https://github.com/c4pt0r/agfs

## FUSE is All You Need

- Jakob Emmerling，2026-01-11：为代理通过文件系统访问一切。
- 总结近期依赖 shell+FS 的代理框架：Turso AgentFS、Anthropic Agent SDK、Vercel 等。
- 展示文件系统用于长上下文处理、scratch 规划、按需披露；示例用 FUSE 将邮件域暴露为目录与文件。
- 结论：把“万物当文件”为代理提供统一、可组合的 UI 层。

链接：https://jakobemmerling.de/posts/fuse-is-all-you-need/
