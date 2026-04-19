# _Aleph 笔记知识库

一个基于 Typora + Git 的个人知识管理（PKM）库，遵循「输入 → 加工 → 输出」三层结构

---

## 一、文件夹结构

```
_Aleph/
├── README.md
├── docs/                       # 笔记主体（加工层）
│   ├── _schema.md              # 笔记体系规范
│   ├── _wiki.md                # 知识库主页 / 模型对照基准
│   ├── _dashboard.md           # 仪表盘
│   ├── !inbox-问题汇总.md       # 待处理收件箱
│   ├── book-@*.md              # 读书笔记
│   ├── ref-*.md                # 外部参考摘要
│   ├── tracking-@*.md          # 行动记录与实践
│   ├── toolkit-@*.md           # 多模型桥接
│   ├── movie-@*.md             # 观影笔记
│   ├── atom-*.md               # 原子笔记（认知摩擦）
│   └── hypo-*.md               # 假设笔记
│
├── raw/                        # 原始素材（输入层）
│   ├── eBook/                  # 电子书（按 PKM 角色分类）
│   │   ├── 00-distilled/       # 已做笔记
│   │   ├── 01-model/           # 待提取模型
│   │   ├── 02-context/         # 背景通识
│   │   ├── 03-literature/      # 文学
│   │   └── 04-pending/         # 暂不处理
│   ├── lit/                    # 学术文献 PDF
│   └── ref/                    # PKM 参考文章 PDF
│
├── print/                      # 导出件（输出层，distill-note-*.docx 等）
├── image-hosting/              # 笔记内嵌图片
├── !template/                  # 笔记模板
├── copilot/                    # Copilot 对话与 Prompt
│
└── .claude/                    # Claude Code 配置
```

**核心约束**：`raw/eBook/00-distilled/` 与 `docs/book-@*.md` 一一对应——读完一本书写完笔记后，电子书从 `01-model/` 移入 `00-distilled/`，闭环完成

---

## 二、笔记分类体系

### 2.1 外部输入类（来自他人观点）

- `book`：读书笔记，主要是「模型提取 + 概念框架」
- `ref`：外部参考，总结文章/视频/资料中的方法与观点
- `tracking`：行动记录、反思、模型迁移与实践反馈
- `toolkit`：多个模型或概念的桥接、综合与工具化

### 2.2 自我认知类（记录认知状态）

- `atom-`：当前真实存在的认知摩擦、问题或困惑
- `hypo-`：基于一个或多个 `atom-` 形成的阶段性假设 / 解释 / 猜想

两点说明：

- `atom-` 与 `hypo-` 不是线性升级关系，而是**循环关系**：`atom- → hypo- → 新的 atom- → 修正 / 替换 hypo-`
- `hypo-` 只是暂时压缩问题的工作模型，**绝不代表这个问题已经得到解决**

---

## 三、统一字段结构

每条笔记建议包含以下字段：

- `title`：标题
- `type`：book / ref / tracking / toolkit
- `coreConcepts`：本笔记的核心模型或关键词列表
- `source`：原始来源或书名/作者
- `appliedModels`：如果是 tracking，则列出应用的模型；如果是 book/ref，则列出可应用的模型
- `actionItems`：可直接落地的行动或实验
- `links`：关联笔记或桥接文档，如 `book-@...` / `ref-...` / `toolkit-@...` / `tracking-@...`
- `comment`：当前状态、疑问、补充说明

---

## 四、层级标签定义

### 4.1 认知层

用于描述「思维结构」、「认知模型」、「决策机制」等。

- 示例：系统 1/2、贝叶斯、自由能、认知偏差、前景理论

### 4.2 行动层

用于描述「执行方法」、「实践路径」、「行动设计」等。

- 示例：刻意练习、MVP、环境设计、决策最小化、SQ3R

### 4.3 系统层

用于描述「体系构建」、「工作流设计」、「长期反馈循环」等。

- 示例：DKIA、输入/处理/输出、认知负荷、知识库结构、工具链
