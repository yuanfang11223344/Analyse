# Analyse 仓库维护规则

## 权威路径

- 本地权威工作树：`/Users/ganxuanzhi/Documents/自动化任务/仓库缓存/分析仓库/analyse-repo`
- GitHub 仓库：`https://github.com/yuanfang11223344/Analyse.git`
- Obsidian 镜像根目录：`/Users/ganxuanzhi/Documents/Obsidian Vault/分析报告`

以后 Analyse 仓库的提交、推送、状态检查和规则更新，都必须优先在本地权威工作树中完成。其他临时克隆目录只可作为加工缓存，不能作为最终维护入口。

## 内容目录

- `reports/`：面向阅读的中文分析报告、逐页读书笔记、总览和索引。
- `sources/`：原文抽取文本、页索引、分段材料等可复查来源。
- `git笔记/`：Git 学习笔记，按该目录内 `MAINTENANCE.md` 维护。

## 长文档分析流程

1. 确认源文件路径、页数、语言和输出目标。
2. 长 PDF 必须按页或按小批次处理；需要逐页读书笔记时，每页单独生成 Markdown 和单页截图。
3. 英文材料必须输出中文解读；每页至少包含原文要点、原文解读、我的理解和本页小结。
4. 不使用多页拼接图替代逐页分析；拼接图只可作为辅助预览，不作为主要报告。
5. 更新 `reports/` 后，同步更新对应 `sources/`、索引和总览。
6. 同步 Obsidian 镜像，保持本地仓库和笔记库内容一致。
7. 提交前展示 `git status` 和变更摘要；收到确认后再 commit 和 push。

## Git 规则

- 默认分支：`main`
- 远端：`origin`
- 提交信息建议：
  - `analysis: <变更描述>`
  - `git笔记: <变更描述>`
  - `maintenance: <变更描述>`
- 不提交 `.DS_Store`、临时文件、未确认的大型中间文件。
- 推送前确认当前目录是本地权威工作树。

## 当前约定

- `Design Compiler Training Fudan` 报告采用逐页读书笔记结构。
- 对应 Obsidian 镜像目录：`/Users/ganxuanzhi/Documents/Obsidian Vault/分析报告/DC综合学习/Design Compiler Training Fudan`
