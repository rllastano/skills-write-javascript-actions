<header>

<!--
  <<< Author notes: Course header >>>
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses MIT license.
-->

[English](https://github.com/skills/write-javascript-actions) | 中文

> 本课程翻译自 Github Skills，全部课程请点击 [这里查看](https://www.github-zh.com/getting-started)

# 编写 JavaScript Actions

_编写属于自己的 GitHub JavaScript Action，用它来自动化你的工作流程。_

</header>

<!--
  <<< Author notes: Course start >>>
  Include start button, a note about Actions minutes,
  and tell the learner why they should take the course.
-->

## Welcome

在这门课程中，你将学习如何编写并发布属于你自己的 JavaScript Action，来定制你的工作流程。

- **目标人群**：开发者、GitHub 用户、Git 新手、学生、项目管理者以及团队成员。
- **你将学到**：如何在工作流文件中使用现有的 Actions，以及如何创建自定义的 JavaScript Action，并将它发布到 GitHub Marketplace。
- **先决条件**：在开始之前，你需要对 GitHub、GitHub Actions 以及持续集成（CI）有基本了解。
- **课程时长**：大约需要 1 到 2 小时完成课程。

在本课程中，你将：

1. 初始化一个 JavaScript 项目
2. 配置一个 Action
3. 创建元数据文件
4. 编写 JavaScript 脚本
5. 在 workflow 文件中添加 Action
6. 触发 Action 运行

### 开始学习本课程

<!-- For start course, run in JavaScript:
'https://github.com/new?' + new URLSearchParams({
  template_owner: 'skills',
  template_name: 'write-javascript-actions',
  owner: '@me',
  name: 'skills-write-javascript-actions',
  description: 'My clone repository',
  visibility: 'public',
}).toString()
-->

[![start-course](https://user-images.githubusercontent.com/1221423/235727646-4a590299-ffe5-480d-8cd5-8194ea184546.svg)](https://github.com/new?template_owner=github-china&template_name=write-javascript-actions&owner=%40me&name=skills-write-javascript-actions&description=My+clone+repository&visibility=public)

1. 右键点击上方 **Start course** 按钮，选择在新标签页中打开链接。
2. 在新页面中根据系统提示新建一个仓库。
   - 仓库名称、描述这些字段系统已经帮我们自动填充好了，您可以按需修改。
   - 建议选择公开仓库，因为私有仓库有[GitHub Actions 分钟数限制](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions)。
   - 最后点击 Create repository 按钮
3. 仓库创建完毕后，等待大约 20 秒（等待Action执行），然后刷新页面。注意是刷新您仓库的页面，不是本课程的页面。如果页面没有变化，请继续等待。然后按照 README 中的步骤一步步进行。

<footer>

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/write-javascript-actions) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
