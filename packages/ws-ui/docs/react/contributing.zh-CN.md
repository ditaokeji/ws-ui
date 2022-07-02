---
order: 12
title: 贡献指南
toc: false
---

这篇指南会指导你如何为 ws-ui 贡献一份自己的力量，请在你要提 issue 或者 pull request 之前花几分钟来阅读一遍这篇指南。

## 分支管理

基于我们的 [发布周期](/changelog)，我们长期维护两个分支 `master` 和 `feature`。如果你要修一个 bug，那么请发 pull request 到 `master`，我们会每周从 master 发布一个 patch 版本；如果你要提一个增加新功能的 pull request，那么请基于 `feature` 分支来做，每月末我们会合并 feature 到 master，并发布一个包含新特性的 minor 版本。

## 第一次贡献

如果你还不清楚怎么在 GitHub 上提 Pull Request ，可以阅读下面这篇文章来学习：

[如何优雅地在 GitHub 上贡献代码](https://segmentfault.com/a/1190000000736629)

## Pull Request

ws-ui 团队会关注所有的 pull request，我们会 review 以及合并你的代码，也有可能要求你做一些修改或者告诉你我们为什么不能接受这样的修改。

**在你发送 Pull Request 之前**，请确认你是按照下面的步骤来做的：

1. 基于 [正确的分支](#分支管理) 做修改。
1. 在项目根目录下运行了 `npm install`。
   > 在 Windows 10 开发环境下，如果出现 `gyp err! find vs msvs_version not set from command line or npm config`错误, 请在运行 `npm install` 前安装 [最新版 Python v3](https://www.python.org/downloads/)， 并通过 [Visual Studio Installer](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio?view=vs-2019#step-3---install-the-visual-studio-installer) 安装 **Desktop development with C++**。
1. 如果你修复了一个 bug 或者新增了一个功能，请确保写了相应的测试，这很重要。
1. 确认所有的测试都是通过的 `npm run test`。 小贴士：开发过程中可以用 `npm test -- --watch TestName` 来运行指定的测试。
1. 运行 `npm test -- -u` 来更新 [jest snapshot](http://facebook.github.io/jest/docs/en/snapshot-testing.html#snapshot-testing-with-jest) 并且把这些更新也提交上来（如果有的话）。
1. 确认所有的 UI 改动通过 `npm run test-image`，可以运行 `npm run test-image -- -u` 更新 UI 快照并且把这些更新也提交上来（如果有的话），**UI 测试基于 [Docker](https://docs.docker.com/get-docker/)，根据平台下载对应的安装程序。**
1. 确保你的代码通过了 lint 检查 `npm run lint`. 小贴士: Lint 会在你 `git commit` 的时候自动运行（通过[Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)）。

## 开发流程

在你 clone 了 ws-ui 的代码并且使用 `npm install` 安装完依赖后，你还可以运行下面几个常用的命令：

1. `npm start` 在本地运行 ws-ui 的网站。
2. `npm run lint` 检查代码风格。
3. `npm test` 运行测试。(在运行测试前请确保 `NODE_ENV` 环境变量没有被设定，否则可能会引发一些问题)
4. `npm run compile` 编译 TypeScript 代码到 lib 和 es 目录。
5. `npm run dist` 构建 antd 的 UMD 版本到 dist 目录。

### 切换主题

在启动时，设置需要执行的主题：

```bash
DEV_THEME=dark npm start
```

访问 [http://127.0.0.1:8001/components/button-cn/?theme=dark](http://127.0.0.1:8001/components/button-cn/?theme=dark)。

