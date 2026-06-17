# Git提交规范

## 意义及现状

在开发过程中，Git每次提交代码，都需要写Commit message（提交说明），规范的Commit message有很多好处：

- 方便快速浏览查找，回溯之前的工作内容
- 可以直接从commit 生成Change log(发布时用于说明版本差异)

## 规范方式

使用[commitlint](https://link.juejin.cn?target=https%3A%2F%2Fmarionebl.github.io%2Fcommitlint%2F%23%2F)和[husky](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Ftypicode%2Fhusky) 来进行提交检查，当执行`git commit`时会在对应的git钩子上做校验，只有符合格式的Commit message才能提交成功。

增加[commitizen](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Fcommitizen%2Fcz-cli)支持，使用[cz-customizable](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Fleonardoanalista%2Fcz-customizable)进行配置。支持使用`git cz`替代`git commit`。

## Commit message 格式

```
<type>(<scope>): <subject>
// 注意冒号 : 后有空格
// 如 feat(miniprogram): 增加了小程序模板消息相关功能
```

**scope选填**表示commit的作用范围。**subject必填**用于对commit进行简短的描述。**type必填**表示提交类型：

- feat - 新功能 feature
- fix - 修复 bug
- docs - 文档注释
- style - 代码格式(不影响代码运行的变动)
- refactor - 重构、优化(既不增加新功能，也不是修复bug)
- perf - 性能优化
- test - 增加测试
- chore - 构建过程或辅助工具的变动
- revert - 回退
- build - 打包

## 如何加入项目

```js
// commitlint
npm i commitlint --save-dev
npm i @commitlint/config-conventional --save-dev
// 新建配置文件 commitlint.config.js
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      "feat", "fix", "docs", "style", "refactor",
      "perf", "test", "chore", "revert", "build"
    ]],
    'subject-case': [0]
  }
};

// husky
npm i husky --save-dev
// 在package.json中增加
"husky": {
  "hooks": {
    "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
  }
}

// commitizen
npm install commitizen -g
npm install commitizen --save-dev
commitizen init cz-customizable --save --save-exact
```

## 自动生成Change log

```bash
npm i conventional-changelog-cli --save-dev
# 在package.json中加入
"scripts": {
  "changelog": "conventional-changelog -p angular -i CHANGELOG.md -s"
}
npm run changelog
```
