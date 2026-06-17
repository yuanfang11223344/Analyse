# Git 工具 - 重写历史

> **在满意之前不要推送你的工作。**

## 修改最后一次提交

### 1. 仅修改提交信息

```bash
git commit --amend -m "新的提交信息"
```

### 2. 添加新文件到上次提交

```bash
git add 漏掉的文件.txt
git commit --amend --no-edit
```

### 3. 修改已提交的文件内容

```bash
vim 需要修改的文件.js
git add 需要修改的文件.js
git commit --amend --no-edit
```

### 4. 完全替换上次提交

```bash
git add -A
git commit --amend -m "全新的提交内容"
```

### 5. 修改提交作者

```bash
git commit --amend --reset-author
git commit --amend --author="新作者 <email@example.com>"
```

> **黄金法则**：只对本地未推送的提交使用 `--amend`。已推送的强制覆盖用 `git push --force-with-lease`。

## 修改多个提交信息

```bash
git rebase -i HEAD~3  # 修改最近3个提交
```

将需要修改的提交前面的 `pick` 改为 `edit`。保存退出后：

```bash
git commit --amend  # 修改
git rebase --continue  # 继续
```

## 重新排序提交

在 rebase -i 编辑器中重新排列 `pick` 行的顺序即可。删除某行即可移除对应提交。

## 压缩提交

```text
pick f7f3f6d changed my name a bit
squash 310154e updated README formatting
squash a5f4a0d added cat-file
```

保存后 Git 会将三次提交合并为一个，并让你编辑合并后的提交信息。

## 拆分提交

将需要拆分的提交改为 `edit`：

```text
pick f7f3f6d changed my name a bit
edit 310154e updated README formatting and added blame
pick a5f4a0d added cat-file
```

然后：

```bash
git reset HEAD^
git add README
git commit -m 'updated README formatting'
git add lib/simplegit.rb
git commit -m 'added blame'
git rebase --continue
```

## filter-branch / filter-repo

> `git filter-branch` 有很多陷阱，不再推荐使用。建议用 `git-filter-repo`：https://github.com/newren/git-filter-repo

### 从每一个提交中移除一个文件

```bash
git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
```

### 使一个子目录做为新的根目录

```bash
git filter-branch --subdirectory-filter trunk HEAD
```

### 全局修改邮箱地址

```bash
git filter-branch --commit-filter '
        if [ "$GIT_AUTHOR_EMAIL" = "schacon@localhost" ];
        then
                GIT_AUTHOR_NAME="Scott Chacon";
                GIT_AUTHOR_EMAIL="schacon@example.com";
                git commit-tree "$@";
        else
                git commit-tree "$@";
        fi' HEAD
```
