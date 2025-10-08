---
layout: post
title: "SolidDesigner 架构速记：命令/交互/插件三件套"
date: 2025-10-08
categories: [architecture]
tags: [C++, CAD, Qt, OCC, architecture]
---

> 目标：在大型 CAD/BIM 平台中实现可扩展、可观测、易迭代的“命令 × 交互 × 插件”体系。

- **命令系统**：ICommand / IAction 分离，统一事务与撤销重做；命令描述（名称、图标、快捷键、上下文）。
- **交互框架**：IInteractionGraph 驱动状态流转，指针/键盘事件统一抽象；选择、预选、拖拽等策略可插拔。
- **插件机制**：IPluginManager 统一生命周期与依赖，跨 DLL 资源与智能指针策略（OwnerPtr/WeakPtr）。
- **诊断与日志**：DBG_WARN/INFO/ERROR 等宏，线程感知弹框与日志下沉，支持环境变量控制与远程回传。

后续文章会逐步拆解各子系统，并给出可编译示例。