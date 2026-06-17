# Git拉取远程指定目录

git1.7之后的版本支持拉取远程仓库的指定目录。

## 操作案例

1. 新建本地文件夹：

```bash
$ mkdir test
$ cd test
$ git init
```

2. 添加远程仓库：

```bash
git remote add origin https://github.com/wangdoc/webapi-tutorial.git
```

3. 启用 `Sparse Checkout` 功能：

```bash
git config core.sparsecheckout true
```

4. 添加想要克隆的目录：

```bash
echo "docs" >> .git/info/sparse-checkout
```

5. 拉取指定目录：

```bash
git pull origin master
```
