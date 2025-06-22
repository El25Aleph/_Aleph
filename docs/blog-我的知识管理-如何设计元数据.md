---
author: me
title: blog-我的知识管理-如何设计元数据与标签
date: 2025-06-22
---

## 0. 动机/背景

正如在上篇所说，今后要使用 obsidian 作为知识管理工具。在 obsidian 中可以给 markdown 文件添加 YAML 属性，其本质是给文档添加一系列的元数据，方便后面使用 dataview 插件进行知识图谱的制作和文档关联的可视化。由此，引出问题：

- 按照 MECE 法则，应该从哪几个维度添加元数据？
- 每一个维度又应该对应哪些内容？
- 如何建立标签系统？

DeepSeek 为我分了五个维度，分别是：

- 来源维度 (Source Dimension)：知识从哪来？
- 内容维度 (Content Dimension)：如何（在知识网络中）快速识别知识？
- 认知维度 (Cognitive Dimension)：我与知识是什么关系？
- 关系维度 (Relation Dimension)：当前知识位于知识网络的什么位置？
- 管理维度 (Management Dimension)：如何管理知识？

知识管理的精髓，根据客观存在和主观意识，分为三类：

- 物理存在
- 逻辑本质
- 认知映射

按照这个原则，分别对应这五个维度：

- 物理坐标：来源维度 + 管理维度 **→ 笔记实体**
- 逻辑坐标：内容维度（面 → 点） + 关系维度（点 → 面） **→ 知识本质**
- 认知坐标：关联行动，为下一个工作流创造灵感/动机/问题，最终形成闭环

```mermaid
graph TD
    A[知识实体] -->|客观存在| B["物理坐标<br>（笔记DNA）"]
    A -->|抽象表达| C["逻辑坐标<br>（知识星图）"]
    A -->|主观转化| D["认知坐标<br>（掌握光谱）"]
    
    D -->|行动触发| E[新工作流循环]
    
    classDef entity fill:#E3F2FD,stroke:#90CAF9
    classDef physical fill:#FFCCBC,stroke:#FF5722
    classDef logical fill:#C8E6C9,stroke:#4CAF50
    classDef cognitive fill:#F8BBD0,stroke:#E91E63
    classDef action fill:#B2EBF2,stroke:#00BCD4
    
    class A entity
    class B physical
    class C logical
    class D cognitive
    class E action
```

对于认知坐标，DeepSeek 用一个例子说明：

```mermaid
graph TB
    D[认知坐标]
    D --检测到confidence=2--> D2["添加!知识缺口标签"]
    D2 --> D3["生成行动项：<br>“验证[[元认知]]在晨间规划的应用”"]
    D3 --> E1[输出层]
    E1 -->|行动记录| F[动机层]
    F -->|新问题| G[输入层]
    
    classDef gap fill:#FFF59D,stroke:#F57F17
    classDef action fill:#81D4FA,stroke:#0288D1
    class D2 gap
    class D3 action
```

最后，DeepSeek 总结了元数据是如何在“法-术-器”层面起作用的：

```mermaid
graph TB
    A[“物理存在”] -- 固化 --> B[知识实体]
    C[“逻辑关系”] -- 连接 --> B
    D[“主观认知”] -- 活化 --> B
    
    B -- 反哺 --> E[行动实践]
    E -- 更新 --> D
```

引用 DeeSeek 的一段话：

>当您打开Obsidian时：
>
>- 您看到的是**物理坐标**（笔记元数据）
>- 您思考的是**逻辑坐标**（知识网络）
>- 您创造的是**认知坐标**（个人理解）

在认知维度，存在知识管理中最大的挑战——**如何将主观认知客观化**？

## 1. 来源维度 

| 字段              | 说明         | 示例                                      | 必要性   |
| :---------------- | :----------- | :---------------------------------------- | :------- |
| `sourceType`      | 载体类型     | `book`/`podcast`/`video`/`paper`/`course` | 必填     |
| `sourceTitle`     | 来源完整名称 | 《认知觉醒》/《Lex Fridman Podcast》      | 必填     |
| `sourceCreator`   | 创作者       | 周岭/Lex Fridman                          | 必填     |
| `sourcePublisher` | 出版方/平台  | 中信出版社/YouTube                        | 选填     |
| `sourceDate`      | 来源发布时间 | `2020-03`                                 | 选填     |
| `sourceLink`      | 来源链接     | [URL]                                     | 强推     |
| `sourceISBN`      | 书籍唯一标识 | `9787508660752`                           | 书籍必填 |
| `sourceDOI`       | 论文标识     | `10.1016/j.tics.2021.06.001`              | 论文必填 |

## 2. 内容维度 

| 字段            | 说明            | 示例                                                         | 必要性 |
| :-------------- | :-------------- | :----------------------------------------------------------- | :----- |
| `coreConcept`   | 核心概念/模型名 | 艾宾浩斯遗忘曲线/二八法则                                    | 必填   |
| `knowledgeType` | 知识分类        | `concept`/`model`/`method`/`principle`/`case`/`quote`/`data` | 必填   |
| `domain`        | 所属领域        | `认知科学`/`经济学`/`AI`                                     | 必填   |
| `abstract`      | 一句话摘要      | 描述遗忘规律的记忆模型                                       | 强推   |
| `keyDiagram`    | 核心图表代码    | ````mermaid graph LR...`                                     | 强推   |
| `complexity`    | 理解难度        | `1-5`分                                                      | 选填   |

## 3. 认知维度

| 字段            | 说明         | 示例                                                 | 必要性 |
| :-------------- | :----------- | :--------------------------------------------------- | :----- |
| `maturity`      | 笔记成熟度   | `seedling`(初稿)/`budding`(发展中)/`evergreen`(完善) | 必填   |
| `lastReviewed`  | 最后复习时间 | `2023-08-20`                                         | 必填   |
| `confidence`    | 掌握置信度   | `1-5`分                                              | 强推   |
| `knowledgeGaps` | 知识缺口     | ["神经机制不明","缺少案例"]                          | 选填   |
| `actionItems`   | 行动项       | ["实践费曼技巧","验证模型"]                          | 强推   |

## 4. 关系维度

| `parentNote`      | 关联原始笔记 | `[[note-认知科学]]`           | 必填 |
| ----------------- | ------------ | ----------------------------- | ---- |
| `childCards`      | 衍生知识卡片 | `[[card-工作记忆]]`           | 选填 |
| `relatedConcepts` | 相关概念     | `[[刻意练习]]`,`[[心流]]`     | 强推 |
| `opposingViews`   | 对立观点     | `[[行为主义学习论]]`          | 强推 |
| `appliedIn`       | 应用场景     | `[[写作技巧]]`,`[[项目管理]]` | 强推 |

## 5. 管理维度

| 字段          | 说明       | 示例               | 必要性 |
| :------------ | :--------- | :----------------- | :----- |
| `cardID`      | 卡片唯一ID | `CRD-2023-B001`    | 必填   |
| `createdTime` | 创建时间   | `2023-08-20T14:30` | 必填   |
| `updatedTime` | 更新时间   | `2023-09-15T10:22` | 必填   |
| `curator`     | 整理者     | 您的姓名           | 选填   |
| `version`     | 版本号     | `v1.2`             | 强推   |

## 6. 标签系统

- 使用三级层级标签
- 特殊标签前缀：
  - `!`
  - `$`
  - `@`