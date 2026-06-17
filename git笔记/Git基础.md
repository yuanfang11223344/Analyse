# Git基础

## Git文件的三种状态和工作模式

- Workspace：工作区
- Index / Stage：暂存区
- Repository：仓库区（或本地仓库）
- Remote：远程仓库

## 一、新建代码库

```bash
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]

# 下载指定的分支
$ git clone -b [branchName] [url]
```

## 二、配置

```bash
# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

## 三、增加/删除文件

```bash
$ git add [file1] [file2] ...
$ git add [dir]
$ git add .
$ git rm -r [file1]
```

## 四、代码提交

```bash
$ git commit -m [message]
$ git commit [file1] [file2] ... -m [message]
$ git commit -a
$ git commit -v
$ git commit --amend -m [message]
$ git commit --amend [file1] [file2] ...
```

## 五、分支

```bash
$ git branch --show-current
$ git branch
$ git branch -r
$ git branch -a
$ git branch [branch-name]
$ git checkout -b [branch]
$ git branch [branch] [commit]
$ git branch --track [branch] [remote-branch]
$ git branch -m old_branch new_branch  # 重命名分支
$ git checkout [branch-name]
$ git branch --set-upstream [branch] [remote-branch]
$ git merge [branch]
$ git cherry-pick [commit]
$ git branch -d [branch-name]
$ git push origin --delete [branch-name]
$ git push origin :[branch-name]
$ git branch -dr [remote/branch]
```

## 六、标签

```bash
$ git tag
$ git tag [tag]
$ git tag [tag] [commit]
$ git tag -d [tag]
$ git push origin :refs/tags/[tagName]
$ git show [tag]
$ git push [remote] [tag]
$ git push [remote] --tags
$ git checkout -b [branch] [tag]
```

## 七、查看信息

```bash
$ git status
$ git log
$ git log --stat
$ git log -S [keyword]
$ git log [tag] HEAD --pretty --oneline
$ git log --follow [file]
$ git log -p [file]
$ git log -5 --pretty --oneline
$ git shortlog -sn
$ git blame [file]
$ git diff
$ git diff --cached [file]
$ git diff HEAD
$ git diff [first-branch]...[second-branch]
$ git show [commit]
$ git show --name-only [commit]
$ git show [commit]:[filename]
$ git reflog
```

## 八、远程同步

```bash
$ git fetch [remote]
$ git remote add origin [remote]
$ git remote remove origin
$ git remote -v
$ git remote show [remote]
$ git remote add [shortname] [url]
$ git pull [remote] [branch]
$ git push [remote] [branch]
$ git push origin [branch]
$ git push [remote] --force
$ git push [remote] --all
```

## 九、撤销

```bash
$ git checkout [file]
$ git checkout [commit] [file]
$ git checkout .
$ git reset HEAD
$ git reset --hard HEAD~1
$ git reset [file]
$ git reset --hard
$ git reset [commit]
$ git reset --hard [commit]
$ git reset --keep [commit]
$ git revert [commit]
$ git stash
$ git stash pop
```

## 通过ssh推送到远程

1. 生成密钥：`ssh-keygen -t rsa -C "邮箱地址"`
2. 绑定公钥到远程仓库
3. 测试：`ssh -T git@github.com`
4. 推送使用SSH地址

## 分支的合并操作

```bash
# 需求：在 develop 上创建 bugfix 分支，修复后合并回 develop

git branch bugfix
git checkout bugfix
git push origin bugfix

# 修复完成...
git add .
git commit -m 'fix bug'

# 合并回 develop
git checkout develop
git pull origin develop
git merge bugfix
git push origin develop

# 删除分支
git branch -d bugfix
git push --delete origin bugfix
```

## 分支冲突

### 本地分支冲突
当分支和主干修改同一行内容时，合并会产生冲突。进入冲突文件修改然后提交。

### 多人协作冲突
解决办法：推送前先pull拉取，保证是最新代码，然后push推送。
