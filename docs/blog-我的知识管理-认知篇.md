---
title: blog-我的知识管理-认知篇
author: me
data: 2024-11-30
---

框架：

```mermaid
%%{init:{'theme': 'neutral'}}%%
flowchart TD
    确定目标@{ shape: stadium, label: "1.确定目标" }
    subgraph 1[4.学以致用]
    刻意练习@{ shape: stadium, label: "刻意练习 + MVP" }
    %%MVP@{ shape: stadium, label: "MVP" }
    end
    subgraph 2[2.主动输入]
    批判性思维@{ shape: stadium, label: "无利不起早 + 批判性思维" }
    %%无利不起早@{ shape: stadium, label: "无利不起早" }
    end
    subgraph 3[3.知识体系]
    长青笔记@{ shape: procs, label: "长青笔记" }
    大纲笔记@{ shape: procs, label: "大纲笔记" }
    临时笔记@{ shape: procs, label: "临时笔记" }
    direction LR
        %%长青笔记 --> 大纲笔记
        %%大纲笔记 --> 长青笔记
        subgraph 4[层级结构]
        长青笔记
        end
        %%大纲笔记 --> 临时笔记
        %%临时笔记 --> 大纲笔记
        subgraph 5[网状结构]
        临时笔记
        end
    %%临时笔记 --> |渐进式阅读|长青笔记
    4 --> 大纲笔记 --> 5
    5 --> 大纲笔记 --> 4
    5 --> |渐进式阅读|4

    end
确定目标 --> 2 --> 3 --> 1
````
