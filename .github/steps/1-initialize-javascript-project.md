<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
-->

## Step 1: 初始化 JavaScript 项目

_欢迎来到本课程 :tada:_

### 配置工作流

GitHub 仓库默认已经启用了 Actions，但要让它实际运行，还需要告诉仓库“应该执行什么”。具体做法是在仓库中创建一个工作流（workflow）文件来实现。

Workflow 文件用于描述自动化流程，它由 jobs（任务）和 steps（步骤）组成，以及触发执行所需的条件。

一个仓库中可以包含多个 **workflow** 文件，用于执行不同的任务。因此，在命名工作流文件时，应确保名称能准确反映其执行的任务内容。

> 在本课程中，我们会为了教学方便，将多个任务都放在同一个 workflow 文件中，这在实际项目中并不推荐。

了解更多：[关于工作流 (workflows) 官方文档](https://docs.github.com/en/actions/writing-workflows/about-workflows)

## 准备你的开发环境

在接下来的练习中，我们将使用 [GitHub ToolKit](https://github.com/actions/toolkit) 来开发 JavaScript Actions。

这是一个外部依赖库，需要通过 `npm` 安装，因此你的电脑上必须先安装 [Node.js](https://nodejs.org/)。

我们推荐在本地环境中编写 Action，而不是直接在 GitHub 的网页端操作。这样你可以使用自己熟悉的编辑器、插件等让开发更高效。

如果你没有 IDE 偏好，建议使用 [Visual Studio Code](https://code.visualstudio.com/)，它与本课程的演示保持一致。

## 别忘了准备好你的开发环境

接下来的步骤大部分都需要在本地执行，因此请先确保你在电脑上安装了以下工具：

1. [ ] [Node.js](https://nodejs.org)
2. [ ] [Visual Studio Code](https://code.visualstudio.com/) 或其他编辑器。
3. [ ] [Git](https://git-scm.com/)

### :keyboard: 实操环节：初始化一个新的 JavaScript 项目

在本地安装好以上工具后，按照下面的步骤创建你的第一个 Action：

1. 打开终端（macOS / Linux）或命令提示符（Windows）。
2. 克隆当前练习仓库到本地：
   ```shell
   git clone <this repository URL>.git
   ```
3. 进入刚刚克隆的仓库目录：

   ```shell
   cd <local folder with cloned repo>
   ```
4. 切换到 `main` 分支：

   ```shell
   git switch main
   ```
5. 创建一个新文件夹，用于存放我们的 Action 文件：

   ```shell
   mkdir -p .github/actions/joke-action
   ```
6. 进入刚创建的 `joke-action` 文件夹：

   ```shell
   cd .github/actions/joke-action
   ```
7. 初始化 Node.js 项目（使用默认配置）：

   ```shell
   npm init -y
   ```
8. 使用 `npm` 安装所需依赖：[GitHub ToolKit](https://github.com/actions/toolkit) 相关包以及请求库：

   ```shell
   npm install --save request request-promise @actions/core
   ```
9. 将新增的文件提交到仓库中（我们稍后会处理 node_modules 的上传问题）：

   ```shell
   git add .
   git commit -m 'add project dependencies'
   ```
10. 将修改推送到远程仓库：

    ```shell
    git push
    ```
11. 等待约 20 秒后刷新本页面。[GitHub Actions](https://docs.github.com/en/actions) 会自动检测到你的更改，并进入下一步。