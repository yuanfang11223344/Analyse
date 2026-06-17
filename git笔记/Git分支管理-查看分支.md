# Git分支管理-查看分支

## 查看分支

```bash
$ git branch
  iss53
* master  # 带星号*表示当前所在分支
  testing
```

## 查看每个分支的最后提交

```bash
$ git branch -v
  iss53   93b412c fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 test
```

## 查看已(未)合并的分支

```bash
$ git branch --merged # 查看已合并分支列表
  iss53
* master
```

分支名字前没有 `*` 号的分支通常可以使用 `git branch -d` 删除掉。

```bash
$ git branch --no-merged # 查看未合并的分支列表
  testing
```

强制删除未合并的分支：

```bash
$ git branch -D testing
```

## 查看指定分支的已(未)合并的分支

```bash
$ git branch --no-merged testing
  topicA
  featureB
```

可以提供一个附加的参数来查看其它分支的合并状态而不必检出它们。
