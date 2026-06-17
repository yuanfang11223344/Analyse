# 解决git大小限制(10053)

## 解决github提交项目时出现10053的问题

1、首先输入如下命令：

```bash
git config http.sslVerify "false"
```

若出现 `fatal: not in a git directory` 错误，继续执行：

```bash
git config --global http.sslVerify "false"
```

2、文件大小的上限设置：

```bash
git config --global http.postBuffer 524288000
```

3、如果git代码还是下载失败，则需要继续修改git缓存的大小。
