# my-skills

可通过 [Skills CLI](https://github.com/vercel-labs/skills) 安装的个人 Agent Skills。

## make-teacher

把本地文件夹初始化为一门可持续学习的技术课程：参考真实课程设计大纲，自动维护主线笔记与进度，用可视化和操作任务辅助教学，并可按需同步 Notion。

### 安装到 Codex

```bash
npx skills@latest add Valkure-Yip/my-skills --skill make-teacher -g -a codex
```

命令为 `skills`（复数）。省略 `-g` 可安装到当前项目；安装后在新会话中调用。

### 使用

在课程文件夹中告诉 Codex：

```text
$make-teacher 帮我创建一门数据库原理与 PostgreSQL 实践课程。
我会写 Python 和基本 SQL，希望能解释事务与索引，并独立分析慢查询。
每周 4 小时，使用本机环境。请先生成课程，再开始第一步。
```

需要 Notion 时在初始化请求中补充：

```text
同时把课程笔记同步到 Notion，在这个页面下创建课程主页：<你的页面链接>。
```

需要可用且有权限的 Notion 连接。未启用时不写入 Notion。初始化后说“继续学习”即可；引申问题结束后默认回到主线。

### 课程只维护五项

```text
AGENTS.md       # 教学方法与保存规则
COURSE.md       # 目标、背景、资料、约束和可选 Notion 配置
SYLLABUS.md     # 固定大纲 + 可更新进度区
TODO.md         # 当前主线位置、覆盖进度、能力验收与后续任务
lessons/        # 课件、练习、证据和交互产物
```

课程大纲定版后，日常只更新进度区；内容与证据放在课件中。分别记录“讲到了”和“独立通过了”。引申问题与回答默认不保存，也不会自动进入延伸清单；用户明确要求时才记。

启用 Notion 后：

```text
指定位置
└── 课程主页（COURSE 内容）
    ├── SYLLABUS
    ├── TODO
    └── lessons
        ├── L01 · 单元名称
        └── L02 · 单元名称
```

没有独立状态文件、日志、锁或校验脚本。课程恢复依赖每轮读取 TODO 和相关课件；跨会话恢复主线，不恢复未保存的引申问答。

### 安装前查看

```bash
npx skills@latest add Valkure-Yip/my-skills --list
```

Skill 入口：[skills/make-teacher/SKILL.md](skills/make-teacher/SKILL.md)。无需发布 npm 包。

## quick-reading

用浅显语言阅读论文、技术博客、文档或 RFC：先总览全文，再按原文章节带读重点、证据与限制，输出 Markdown 文档。复杂内容配合图表、Mermaid 和思维导图；优先使用 XMind MCP，不可用时输出可导入 XMind 的 Markdown。

### 安装到 Codex

```bash
npx skills@latest add Valkure-Yip/my-skills --skill quick-reading -g -a codex
```

### 使用

```text
$quick-reading 带我读懂这篇文章：<文章链接或本地文件路径>
```

保留本机原版教学指令和 Codex 界面元数据。XMind 是可选能力；原文不可访问或缺失关键内容时，应说明缺口，不补造文章结论。

Skill 入口：[skills/quick-reading/SKILL.md](skills/quick-reading/SKILL.md)。
