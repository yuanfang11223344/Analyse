# Git工具-交互式暂存

运行 `git add -i` 进入交互式终端模式：

```
           staged     unstaged path
  1:    unchanged        +0/-1 TODO
  2:    unchanged        +1/-1 index.html
  3:    unchanged        +5/-1 lib/simplegit.rb

*** Commands ***
  1: [s]tatus     2: [u]pdate      3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff        7: [q]uit       8: [h]elp
```

## 暂存与取消暂存文件

- `u` 或 `2`：更新（暂存文件）。输入文件编号选择。
- `r` 或 `3`：撤消（取消暂存）。输入文件编号选择。
- `d` 或 `6`：查看已暂存内容的区别。

## 暂存补丁

输入 `p` 或 `5`（补丁）。Git 会询问你想要部分暂存哪些文件，然后对已选择文件的每一个部分询问：

```
Stage this hunk [y,n,a,d,/,j,J,g,e,?]?
```

选项：
- `y` - 暂存这个区块
- `n` - 不暂存这个区块
- `a` - 暂存这个文件中的所有区块
- `d` - 不暂存这个文件中的任何区块
- `s` - 将当前区块拆分为更小的区块
- `e` - 手动编辑当前区块

也可以在命令行中直接使用：

```bash
$ git add -p  # 等价于 git add --patch
$ git reset --patch  # 部分重置文件
$ git checkout --patch  # 部分检出文件
$ git stash save --patch  # 部分暂存文件
```
