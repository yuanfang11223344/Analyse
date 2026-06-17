# Git笔记 维护规则

## 来源

- 原始网站：[夜猫子的知识栈 - Git学习笔记](https://yemao-zi.github.io/note/git/)
- 爬取时间：2026-06-17
- 爬取工具：Claude Code (WebFetch)
- 总计：19 篇 Markdown 文件

## 目录结构

```
git笔记/
├── MAINTENANCE.md              # 本维护规则
├── README.md                    # 文件索引
├── 常用Git命令清单.md
├── Git变基合并.md
├── Git提交规范.md
├── GitHub-Pull-Request教程.md
├── Git基础.md
├── Git分支-分支原理.md
├── Git分支的新建与合并.md
├── Git分支管理-查看分支.md
├── Git分支开发工作流.md
├── Git分支-远程分支.md
├── Git拉取远程指定目录.md
├── Git分支-变基.md
├── Git工具-查看修订版本.md
├── Git工具-交互式暂存.md
├── Git工具-重写历史.md
├── Git工具-重置揭密.md
├── 解决报错超时.md
└── 解决git大小限制.md
```

## 同步目标

| 目标 | 路径 | 方式 |
|---|---|---|
| GitHub 仓库 | `yuanfang11223344/Analyse.git` → `git笔记/` | git push |
| 本地缓存 | `/Users/ganxuanzhi/Documents/自动化任务/仓库缓存/分析仓库/git笔记/` | cp |
| 学习工作区 | `/Users/ganxuanzhi/学习/Git笔记/` | cp (源) |
| Obsidian Vault | `/Users/ganxuanzhi/Documents/Obsidian Vault/Git笔记/` | cp |

## 维护流程

### 新增内容

1. 从源网站爬取新文章 → 保存为 `.md` 文件到学习工作区
2. 更新 git笔记/README.md 索引
3. Git 提交前展示变更摘要，等待确认
4. commit + push 到 Analyse 仓库
5. 同步到 Obsidian Vault 和本地缓存

### 更新已有文件

1. 对比源网站是否有内容更新
2. 如有更新，覆盖对应 `.md` 文件
3. 提交信息格式：`git笔记: 更新 <文件名>`
4. 同步到所有目标位置

### 内容质量检查

- 代码块 (```) 必须配对完整
- Git 命令拼写正确（常见错误：`--globle` → `--global`）
- 每篇末尾有空行（POSIX 标准）
- 原文链接保持有效

## Git 同步规则

- 仓库：`https://github.com/yuanfang11223344/Analyse.git`
- 提交信息格式：`git笔记: <变更描述>`
- 不提交 `.DS_Store`、临时文件
- 提交前展示变更摘要，push 前确认

## 当前状态

- `2026-06-17`：首次爬取 19 篇 Git 学习笔记，存入 git笔记/ 目录
- 内容校验：全部通过（代码块配对、命令拼写、文件完整性）
