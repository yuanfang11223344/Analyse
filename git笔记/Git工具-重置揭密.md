# Git 工具 - 重置揭密

## 三棵树

| 树 | 用途 |
|---|---|
| HEAD | 上一次提交的快照，下一次提交的父结点 |
| Index | 预期的下一次提交的快照（暂存区） |
| Working Directory | 沙盒（工作区） |

## 工作流程

1. 工作目录修改文件 → `git add` 复制到索引
2. `git commit` → 保存提交对象 → 更新分支指针

## 重置的作用

`reset` 做了三个基本操作：

### 第 1 步：移动 HEAD（--soft 在此停止）

```bash
git reset --soft HEAD~  # 撤销上一次 commit，保留暂存区和工作目录
```

### 第 2 步：更新索引（--mixed，默认行为）

```bash
git reset HEAD~  # 撤销 commit 和 add，保留工作目录修改
```

### 第 3 步：更新工作目录（--hard，⚠️危险）

```bash
git reset --hard HEAD~  # 完全撤销，⚠️数据可能丢失
```

> `--hard` 是 `reset` 命令唯一的危险用法，它也是 Git 会真正地销毁数据的仅有的几个操作之一。

## 通过路径来重置

```bash
git reset file.txt  # 等同于 git reset --mixed HEAD file.txt
```

只将 file.txt 从 HEAD 复制到索引中——实际上就是**取消暂存文件**。

```bash
git reset eb43bf file.txt  # 从指定提交拉取文件到索引
```

## 压缩提交

```bash
git reset --soft HEAD~2  # 回退两个提交，保留所有修改在暂存区
git commit  # 重新提交，相当于把两个提交压缩为一个
```

## 检出 vs 重置

| | HEAD | Index | Workdir | WD Safe? |
|---|---|---|---|---|
| `reset --soft [commit]` | REF | NO | NO | YES |
| `reset [commit]` | REF | YES | NO | YES |
| `reset --hard [commit]` | REF | YES | YES | **NO** |
| `checkout <commit>` | HEAD | YES | YES | YES |
| `reset [commit] <paths>` | NO | YES | NO | YES |
| `checkout [commit] <paths>` | NO | YES | YES | **NO** |

关键区别：
- `reset` 移动 HEAD 分支的指向
- `checkout` 移动 HEAD 自身
- `reset --hard` 不安全；`checkout` 安全（会检查不会覆盖已修改文件）
