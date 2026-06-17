# GitHub Pull Request 教程

## PR五步走

1. 先 fork 别人的项目到自己的仓库中去
2. clone 到本地进行修改
3. 修改完 bug 后，push 回自己的仓库
4. Pull Request，相当于请作者看一下自己的修改
5. 作者 Merge 到 master 上，而你也成了这个项目的 contributor

### 第一步：fork 项目到自己的仓库中

在项目名称右边有 fork 键，登录后点击即可。

### 第二步：将项目下载到本地

```bash
git clone https://github.com/taotianli/Virgilio.git
```

### 第三步：进入本地文件，并进行相应修改

```bash
cd Virgilio/
git add README.md
git commit -m 'Modefied the README.'
```

### 第四步：上传到自己的 GitHub 仓库，并申请 Pull Request

```bash
git push origin master
```

之后就可以申请 PR 了。点击 `Pull Request -> New Pull Request`。

> **注意**：在作者合并之前，你可以做多次修改，在申请 PR 后只要 push 回自己的仓库，GitHub 会自动记录修改并同步。

**总结**：fork → clone → add & push → PR → merged
