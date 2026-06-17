# Git分支的新建与合并-分支操作

## 创建分支并切换

```bash
$ git checkout -b iss53  # b表示branch
```

等价于：

```bash
$ git branch iss53
$ git checkout iss53
```

## 切换分支

```bash
$ git checkout master
```

在切换到`master`之前，需要`iss53`分支保持好一个干净的状态（修改都已提交）。**注意：切换分支Git 会重置你的工作目录。**

> `checkout` 中文含义 "检出"，`checkout <branch>` 检出分支 => 检出指定分支的代码 => 重置工作目录并切换分支。

接下来，建立一个 `hotfix` 分支修复紧急问题：

```bash
$ git checkout -b hotfix
$ echo 'test' > ./hotfix.txt
$ git add .
$ git commit -m 'fixed'
```

## 合并分支

```bash
$ git checkout master # 首先切回master分支
$ git merge hotfix # 把 hotfix 分支合并过来
```

## 删除分支

```bash
$ git branch -d hotfix # d表示delete
$ git checkout iss53 # 然后切回iss53继续工作
```

## 多次提交之后合并分支

当 `master` 分支所在提交并不是 `iss53` 分支所在提交的直接祖先时，Git 会使用两个分支的末端所指的快照以及这两个分支的公共祖先，做一个简单的**三方合并**。Git 将此次三方合并的结果做了一个新的快照并且自动创建一个新的提交指向它——这个被称作一次合并提交，它的特别之处在于他有不止一个父提交。

## 遇到冲突时的分支合并

如果你在两个不同的分支中，**对同一个文件的同一个部分进行了不同的修改**，Git 就没法干净的合并它们，就产生了冲突。

```bash
$ git merge iss53
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

使用`git status`查看未合并状态。冲突文件中会包含特殊区段：

```
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
```

需要**手动解决冲突**，解决了所有文件里的冲突之后，对每个文件**使用 `git add` 命令**来将其标记为冲突已解决。然后输入 `git commit` 来完成合并提交。
