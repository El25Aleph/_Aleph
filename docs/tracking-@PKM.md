# 2026

## 2026-05-01

先回答 2026-04-08 中的问题：是否要使用 `openclaw`作为 PKM 智能体？答案：不用

这半个月以来下载了 Claude Code CLI, 白嫖宝文的 pro max, 目前感觉效果还不错

回顾 Claude 对话，目前确定了 PKM 的三个维度，以及对应的工具：

| 维度   | 工具           |
| ------ | -------------- |
| 写作层 | Typora         |
| 思考层 | Obsidian       |
| 储存层 | markdown + Git |

终归还是用上了 Obsidian, 但是要明确它的边界

于是我先关闭了第三方插件，只使用它的核心插件：

- Outline
- Backlink
- Graph View
- Canvas

如果后面还有应用场景，考虑开启第三方插件，使用 excalidraw 和 markmap

Obsidian 的功能有两个：

- 默认阅读模式，而非编辑模式，作为 viewer 使用
- 画布功能作为 moc 或者 toolkit 的 draft version

---

这个问题：

> 使用 notion 的多维表格功能记录模型的使用场景和边界条件？

其实算是上面工具篇，思考层的一个潜在延伸

鉴于现在添加了 card-@ 笔记，viewer 其实可以再广泛一点

我的直觉告诉我，notion 可以做两件事：

- 多维表格适合记录 card-@ 和 toolkit-@, 因为它们是已经结构化的东西
- ToDo/看板/日历适合可视化 tracking-@

当然了，这些东西目前在 obsidian 上也不是不能做

但是和 notion 最大的区别还是在于，obsidian 是笔记，只要不改变笔记的内容，怎么渲染都是“死”的

notion 更像是一个人机交互的界面，我可以移动，增改内容

曾经，我的担心在于，notion 和 markdown 两套体系会增加人工维护成本

现在有了 Claude CLI, 也许 AI 可以直接连接 notion 的 API 实现连接？这不仅是单向的，AI 读取 markdown 然后在 notion 中生成多为表格，我在 notion 中给 ToDo 画叉，修改看板的状态等等，也可以通过 AI 来 update 我的 tracking 笔记

这些也都是目前粗浅的想法罢了，也许后面 obsidian 的插件发展起来，不用 notion 也可以实现这些功能了，那就再好不过了

另外，vs code 也可以看 graph view, 只不过效果没有 obsidian 那么好

它独有的优势在于：

1. 严格遵循资源管理器的形式，可以看到 .claude 文件夹
2. 可以一键 git

目前我还是要开三个软件：

- typora 编辑文档
- obsidian 浏览和思考
- vs code 实现同步

目前而言，obsidian 的插件完全可以实现 one for all 的功能，但是我还是不想这么早做改变，先这样吧

其实，这也许涉及到一个更深层次的问题：

- [ ] 如何有效的追踪 tracking-@
- [ ] 光追踪了还不够，行动过后的 lessons learned 如何抽象成 checklist/wiki？

---

在今天和 Claude 对话之前，写了这样一个问题：

> 如何平衡认知负荷与笔记数量？

用我自己的话来说，数量不是关键，而是笔记之间的联系和结构

尽管现在笔记更多了，但是经过 cluster 分类之后，更体系化了

还好我没有东一榔头西一棒槌的乱记，体系就渐渐这样形成了

当然，要永远记住，现在学的知识，没有考试的量化过程，全靠实践去检验。所以知识的理解是非线性，甚至是螺旋的

它会产生复利，在你真正理解它的时候

所以需要笔记来随时告诉大脑：不要让神经元随着时间的流逝被其他垃圾信息占据

## 2026-05-01：与 Claude 对话——cluster / moc / card 体系的渐进式重构

### 起点

90 篇笔记，按认知负荷只能常看 10 篇。表面问题：管理困难、AI 味儿重的笔记懒得读、按学科分类后发现没意义。

### 一、想法的几次反转

**反转 1：分类问题 → 库存问题**

最初我想按"认知层 / 行动层 / 系统层"分类。Claude 反问：90% 笔记从未被回访——这不是分类问题，是**库存问题**。我接受，提出 hot/cold 活跃层思路，限定 10 篇。

**反转 2：冷存档 → 未挖矿石**

我意识到：AI 味儿重的笔记我留着，是期望某天 AI 帮我发现 insight（曾尝试 notebooklm 但因主题太散失焦）。Claude 建议四层结构（活跃 / 矿区 / 文学回响 / 冷存档），矿区按聚焦主题成簇投喂。

**反转 3：自己一晚就把 90 篇分成 12 个 cluster**

我能凭标题回忆内容——证明笔记不是死的，是**缺触发器**。

**反转 4：cluster ≠ moc**

我以为每个 cluster 都要建 moc。Claude 澄清：

- **cluster = 静态聚类**（物理归簇，无独立文件，存于 `!moc-Overview.md` 章节）
- **moc = 问题导航**（必须有驱动问题）

多数 cluster 不需要 moc。现存 6 张 moc 中，只有 [moc-@认知链路](moc-@认知链路.md) 和 [moc-@人性矩阵](moc-@人性矩阵.md) 严格符合定义；其余实际是 dashboard 或 cluster 索引。这一区分写入了 `README §3` 和 `note-intake` agent。

反转 5：表面是 inbox 整理，深层是 tracking 定义混乱

`tracking-@<书名>` 这种"按书做容器"的形式实际承载了 4 种性质不同的内容（思考片段 / 多模型桥接 / 概念结晶过程 / 行动追踪）。我问 Claude 一个根本问题：**知识的最小单元是概念/模型？**

Claude 确认。需要补 `card` 层——这是体系真正缺的一环。

**反转 6：5 张 keystone card 试水（节奏 C）**

不大改 90 篇旧笔记，只挑 5 个核心概念建 card：

- [card-@二八法则](card-@二八法则.md)
- [card-@系统1系统2](card-@系统1系统2.md)
- [card-@贝叶斯更新](card-@贝叶斯更新.md)
- [card-@刻意练习](card-@刻意练习.md)
- [card-@认知偏差清单](card-@认知偏差清单.md)

5 张之间互锚 4-6 次，concept layer 开始自洽。

**反转 7：可视化不够 → 工具分工**

我以为是格式问题（emoji / 序号）。Claude 拆开：**写作流和 review 流应该分工**。Typora 适合写不适合 review；Obsidian 的 Graph view / Canvas 才是 review 工具。所有工具都基于 markdown，可同时打开同目录，不需迁移数据。

### 二、每次反转后的具体动作

| 反转 | 落地动作 |
|------|---------|
| 1-3 | 12 cluster 分类 |
| 4 | 合并 `moc-@逻辑分析` → `moc-@理性思考模型总结`；写入 `README §3` cluster vs moc 边界；新建 `moc-@人性矩阵`（meta 表）；建 `!moc-Overview.md`（双窄表 + 12 cluster 详情） |
| 5 | 4 篇思考延伸 tracking 拆为 4 toolkit + 2 card；删除唯一的 atom（并入本笔记 §2026-04-30 之前条目）；更新 `README §2`（新增 card 层 / 移除 dashboard / 收缩 atom） |
| 6 | 完成 5 张 keystone card |
| 7 | 5 张 card 标题模板化（H2 + § 序号 + 分组水平线）；确定 Typora 写 + Obsidian review 双开方案 |

### 三、最重要的几个判断

1. **笔记的组织轴是概念/主题/模型，不是书**——书只是 input。
2. **cluster ≠ moc ≠ card**——物理归簇 vs 问题导航 vs 单概念结晶；三层语义不同，混用即混乱。
3. **moc 必须有驱动问题**，否则只是个名字花哨的目录。
4. **Don't multi-purpose tools**——Typora 写、Obsidian review、card 是 concept 单元、moc 是 navigation 单元。每个工具 / 笔记类型负责一件事。
5. **AI 味儿的笔记不是垃圾，是未结晶的素材**——补 card 层后，它们成为 toolkit/card 的喂养源。

### 四、当前体系状态

- **94 → ~93 笔记**（增 6 toolkit/card，减 4 旧 tracking + 1 atom）
- **5 张 keystone card** + **6 张 moc** + **12 个 cluster**
- **README §2** 重写为 5 层：输入 / 加工 / 过程 / 自我认知 / 导航
- **`note-intake` agent** 已加入 cluster vs moc 判定标准

### 五、待办（按优先级）

- [ ] **装 Obsidian 双开**（vault = `_Aleph/docs`），用 1 周看 graph view 是否真的解决 review 问题
- [ ] **inbox 残留分流**——按 `!_inbox-问题汇总.md` 顶部 first idea 的 4 类操作
- [ ] **决定是否扩 keystone card 到 7-10 张**——候选：4S/MECE、设计思维、复制因子等
- [ ] **标题模板扩展到 toolkit / book**——暂未做，需单独设计
- [ ] **半年后回看**——长期不动的 cluster 是否归档到 `docs/archive/`

### 六、对自己的提醒

- 重构是一次性动作，体系自洽 ≠ 体系完美。**用起来再迭代**。
- 不要再陷入"鼓捣笔记软件"陷阱——精度通胀的代表反例（参见 [card-@精度操控三型](card-@精度操控三型.md)）。
- card 写完不是结束，是开始——它们应该被反复回访、修改、连接。
