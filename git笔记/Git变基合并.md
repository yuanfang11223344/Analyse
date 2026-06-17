# Git变基合并

## rebase分支合并

### 说明

以下 `v2` 是某个需求的开发分支， `dev`是总的开发分支，`v2` 是基于`dev`分支签出的。

当完成`v2`的开发后，需要把代码合并到`dev`，我们可以使用`rebase`进行合并：

```bash
# 首先将 v2 push到远程仓库
git add .
git commit -m 'xxx'
git push origin v2

# 切换到 dev 拉取最新代码
git checkout dev
git pull origin dev

# 切换到 v2
git checkout v2
git rebase dev # 将 v2 的所有[commit] 变基到(应用到) dev
git rebase --abort # 取消变基

# 切换到 dev
git checkout dev
git merge v2  # 将 dev分支 快进合并

# 查看 原v2的[commit]记录 是否在dev分支的最前面
git log

# 如果到这一步发现有问题，尝试使用 git --abort中止变基，如果还是有问题的可以在dev分支上使用《后悔药》操作
```

#### 变基要遵守的准则

**几个人同时在一个分支上进行开发和提交时，你不要中途执行变基，只有在大家都完成工作之后才可以执行变基。**

**不要基于rebase的分支 切新分支。**

**不要对已经合并到主分支的本地修改进行变基。**

**不要在预发布/正式分支上使用rebase -i。**

#### 变基的实质

变基操作的实质是丢弃一些现有的提交，然后相应地新建一些内容一样但实际上不同的提交。因此，**变基操作过后的分支将不要再使用**。

---

## 后悔药

```bash
# 查看HEAD指针变动记录
git reflog
# 记录示例(当前分支是v2):
07c398f (HEAD -> v2, master) HEAD@{0}: checkout: moving from master to v2
07c398f (HEAD -> v2, master) HEAD@{1}: rebase (finish): returning to refs/heads/master
07c398f (HEAD -> v2, master) HEAD@{2}: rebase (start): checkout v2
15a97d8 HEAD@{3}: reset: moving to 15a97d8
07c398f (HEAD -> v2, master) HEAD@{4}: merge v2: Fast-forward
15a97d8 HEAD@{5}: checkout: moving from v2 to master
07c398f (HEAD -> v2, master) HEAD@{6}: rebase (finish): returning to refs/heads/v2
07c398f (HEAD -> v2, master) HEAD@{7}: rebase (pick): C
15a97d8 HEAD@{8}: rebase (start): checkout master
d278ecd HEAD@{9}: checkout: moving from master to v2
15a97d8 HEAD@{10}: commit: D

# 回退到变基前的状态
git reset --hard d278ecd

# 查看是否回到之前的状态
git log
```

**注意：此操作只能回退当前的分支，如其他分支也要回退，需要切换到该分支并执行上面操作。**

---

## 开发期间的rebase操作

### 背景

`v2` 是基于`dev`切出来的。开发期间，两个分支同时有新的commit：

```
                dev
a - b - c - d - e
        \ - f - g
                v2
```

**需求：把`dev`中新的提交同步到`v2`，且不能影响`dev`分支。**

### 操作步骤

1. 基于最新的 `dev` 切一个新的分支 `dev-copy`

2. 在`dev-copy`中执行rebase，将 `dev-copy` 的提交变基到 `v2`

   ```bash
   git rebase v2 # 将 dev-copy 的提交[commit] 变基到(应用到) v2
   ```

3. 删除原`v2`分支，将`dev-copy`分支名改为`v2`

   ```bash
   git branch -d v2 # 删除分支
   git branch -m dev-copy v2 # 重命名
   ```

---

## git cherry-pick

用于将单个或几个`[commit]`复制到另一个分支。

```bash
git cherry-pick <commitHash> # 将commitHash应用于当前分支
```

git cherry-pick命令的参数不一定是提交的哈希值，分支名也是可以的，表示转移该分支的最新提交。

### 转移多个提交

```bash
git cherry-pick <HashA> <HashB> # A和B提交
git cherry-pick A..B # A到B提交，不包含A
git cherry-pick A^..B # A到B提交，包含A
```

---

## git rebase -i

```bash
git rebase -i master~1 #最后一次
git rebase -i master~5 #最后五次
git rebase -i HEAD~3   #当前版本的倒数第三次状态
git rebase -i commit id #指定的提交位置
```

### 修改历史提交

```bash
1. git rebase -i HEAD~5
2. 将需要修改的commit所在的行前面的 pick 修改为 edit 或者 e
   pick b4ba123435 A
   e 0ae807b99c B
   pick 70890e2e86 C
   pick aa0778f109 D
   pick 630cc16edb E

3. 修改bug代码，如果只需要修改commit信息可以跳过此步
4. git commit --amend
5. 修改commit信息
6. git rebase --continue
```

如果不想继续 rebase：`git rebase --abort`

rebase结束后，所有commitID会被修改，需要强制push：

```bash
git push [仓库名] [分支] -f
```

### rebase -i 操作选项

- `Pick`：会在你的历史记录中保留该提交。
- `Reword`：允许你修改提交信息。
- `Edit`：允许你在重放分支的过程中对提交进行修改。
- `Squash`：可以将多个提交合并为一个。
