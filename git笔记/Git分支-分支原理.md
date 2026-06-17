# Git分支-分支原理

## 首次提交

进行提交操作时，Git 会保存一个提交对象（commit object）。暂存操作为每个文件计算校验和（SHA-1 哈希算法），将文件快照以 **blob 对象** 保存到仓库。

```bash
$ git add README test.rb LICENSE
$ git commit -m 'The initial commit of my project'
```

当执行 `git commit` 时，Git 先计算每个子目录的校验和，保存为**树对象**。随后 Git 创建一个**提交对象**，包含指向该树对象的指针及其他提交信息。

此时仓库中有五个对象：三个 **blob 对象**（保存文件快照）、一个**树对象**（记录目录结构和 blob 对象索引）以及一个**提交对象**。

### 小结：
1. `git add` 暂存操作为每个文件计算校验和，创建每个文件对应的**文件快照（blob对象）**。
2. `git commit` 提交操作计算目录校验和并保存为**树对象**，随后创建一个**提交对象**。

## 再次提交

修改后再次提交，产生的提交对象会包含一个指向上次提交对象（父对象）的指针。

## Git 的分支

Git 分支本质上"仅仅是指向提交对象的可变指针"。默认分支名为 `master`，`master` 分支指针会在每次提交时自动向前移动。

## 创建分支

```bash
$ git branch testing  # 创建新分支，只是一个可移动的新指针
```

## 当前分支的指针

Git 通过名为 `HEAD` 的特殊指针来追踪当前所在分支。`git branch` 命令仅创建新分支，不会自动切换。

## 查看当前所在分支

```bash
$ git log --oneline --decorate
f30ab (HEAD -> master, testing) add feature
34ac2 Fixed bug
98ca9 The initial commit of my project
```

## 分支切换

```bash
$ git checkout testing
```

这样 `HEAD` 就指向 `testing` 分支了。再做一次新的提交，`testing` 分支向前移动，但 `master` 分支仍然指向原来的位置。

切换回 `master` 分支：

```bash
$ git checkout master
```

这条命令做了两件事：一是使 HEAD 指回 `master` 分支，二是将工作目录恢复成 `master` 分支所指向的快照内容。

查看分叉历史：

```bash
$ git log --oneline --decorate --graph --all
* c2b9e (HEAD, master) made other changes
| * 87ab2 (testing) made a change
|/
* f30ab add feature
* 34ac2 fixed bug
* 98ca9 initial commit of my project
```

Git 分支实质上是包含所指对象校验和（长度为 40 的 SHA-1 值字符串）的文件，创建和销毁都极其高效。创建一个新分支相当于往文件中写入 41 个字节（40 个字符和 1 个换行符）。

## 创建分支同时切换

```bash
git checkout -b <newbranchname>
```
