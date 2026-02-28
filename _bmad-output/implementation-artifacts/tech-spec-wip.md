---
title: '红娘配对微信小程序 MVP'
slug: 'matchmaking-miniprogram-mvp'
created: '2026-02-27'
status: 'in-progress'
stepsCompleted: [1]
tech_stack: ['微信小程序原生', 'Vant Weapp', 'Node.js', 'Nest.js', 'PostgreSQL', 'Redis', 'Bull Queue', 'node-cron', '腾讯云']
files_to_modify: []
code_patterns: []
test_patterns: []
---

# Tech-Spec: 红娘配对微信小程序 MVP

**Created:** 2026-02-27

## Overview

### Problem Statement

需要从零开始构建一个红娘配对微信小程序 MVP，包括前端小程序、后端服务、数据库和批处理任务。目前项目是全新的，没有任何代码基础。需要完整的微信生态注册指引和可实施的技术规格文档。

### Solution

基于腾讯云生态构建红娘配对应用：
- **前端**：微信小程序原生开发 + Vant Weapp 组件库
- **后端**：Node.js + Nest.js 框架，提供 RESTful API 和 WebSocket 服务
- **数据库**：PostgreSQL 存储业务数据，Redis 处理缓存和会话
- **批处理**：Bull Queue + node-cron 实现配对算法的定时调度
- **部署**：腾讯云一站式部署（云服务器、云数据库、Redis、COS）

### Scope

**In Scope:**

1. **微信小程序端**
   - 微信授权登录（获取用户信息、手机号）
   - 个人资料编辑（头像、基本信息、兴趣标签）
   - 推荐列表浏览（左滑跳过、右滑喜欢）
   - 用户详情查看
   - 双向匹配通知
   - 一对一聊天（文字+图片）
   - 匹配列表查看

2. **后端服务**
   - 用户认证和授权
   - 用户资料管理
   - 推荐列表 API（调用同事的配对逻辑）
   - 喜欢/跳过操作
   - 双向匹配检测
   - 聊天消息存储和推送
   - WebSocket 实时通信

3. **数据库设计**
   - 用户表
   - 用户资料表
   - 配对记录表
   - 聊天消息表
   - 喜欢/跳过记录表

4. **批处理任务**
   - 定时刷新用户推荐列表
   - 用户活跃度统计
   - 过期数据清理

5. **微信生态注册指引**
   - 微信小程序注册流程
   - 腾讯云服务开通指引
   - 域名配置指南

**Out of Scope:**

- 语音消息、视频通话
- 会员系统/支付功能
- 复杂的高级筛选
- 社交分享功能
- 内容安全审核（使用微信自带 API）
- 数据分析和 BI 看板

## Context for Development

### Codebase Patterns

全新项目，遵循以下技术约定：

**小程序端：**
- 使用微信小程序原生框架
- 组件库：Vant Weapp
- 请求封装：统一 API 调用层
- 状态管理：全局 app.data + 本地 storage
- 代码风格：ES6+，4 空格缩进

**后端：**
- 框架：Nest.js（TypeScript）
- 分层架构：Controller → Service → Repository
- 认证：JWT
- 数据验证：class-validator
- API 规范：RESTful + WebSocket
- 代码风格：Prettier + ESLint

### Files to Reference

| File | Purpose |
| ---- | ------- |
| `_bmad-output/implementation-artifacts/tech-spec-wip.md` | 本技术规格文档（WIP） |
| `_bmad-output/planning-artifacts/wechat-registration-guide.md` | 微信生态注册指引（待生成） |
| `_bmad-output/planning-artifacts/api-specification.md` | API 接口定义（待生成） |

### Technical Decisions

| 决策 | 理由 |
| ---- ---- |
| **微信小程序原生 vs uni-app** | 原生性能更好，微信 API 调用更直接 |
| **Nest.js vs Express** | 结构清晰，适合团队协作，内置依赖注入 |
| **PostgreSQL vs MongoDB** | 关系型数据更适合用户/配对/聊天模型 |
| **Bull Queue vs Agenda** | Bull 基于 Redis，与缓存复用基础设施 |
| **腾讯云 vs 阿里云** | 与小程序生态集成更紧密，一站式管理 |

## Implementation Plan

### Tasks

#### 阶段 1：微信生态注册（待完成）
1. 注册微信小程序账号
2. 完成企业认证
3. 开通腾讯云服务
4. 配置服务器域名

#### 阶段 2：项目初始化（待详细规划）
1. 小程序项目脚手架
2. 后端 Nest.js 项目初始化
3. 数据库 schema 设计
4. Redis 缓存策略设计

#### 阶段 3：核心功能开发（待详细规划）
1. 用户认证模块
2. 个人资料模块
3. 推荐列表模块
4. 匹配逻辑集成
5. 聊天功能

#### 阶段 4：批处理任务（待详细规划）
1. 推荐刷新任务
2. 匹配检测任务
3. 数据清理任务

#### 阶段 5：部署和测试（待详细规划）
1. 腾讯云部署配置
2. API 测试
3. 小程序审核发布

### Acceptance Criteria

（待 Step 2 详细调查后补充）

## Additional Context

### Dependencies

- 微信开发者工具
- Node.js 18+
- PostgreSQL 14+
- Redis 7+
- 腾讯云账号

### Testing Strategy

（待 Step 2 详细调查后补充）

### Notes

- 用户负责：小程序端开发 + 架构调通
- 同事负责：配对算法逻辑
- 后续功能：两人都可参与前后端开发
- 配对逻辑通过 API 调用集成到后端
