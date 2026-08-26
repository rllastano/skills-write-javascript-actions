<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 2: 配置你的 Action

_很好! 继续 :bike:_

我们已经完成前期准备工作，接下来就来创建我们的 **joke-action** 吧。

### :keyboard: 实操环节

接下来的所有步骤都在 `.github/actions/joke-action` 目录下进行。

我们先定义 Action 所**必需的参数**，后续随着功能演进，再逐步添加可选参数。

1. 在 `.github/actions/joke-action` 目录下创建一个新文件 `action.yml`
2. 打开该文件并添加以下内容：

   ```yaml
   name: "my joke action"

   description: "use an external API to retrieve and display a joke"

   runs:
     using: "node16"
     main: "main.js"
   ```

   这段配置的含义是：

   * `name`：Action 的名称（这里叫“my joke action”）；
   * `description`：Action 的简单描述；
   * `runs`：定义运行环境为 Node.js 16，并指定入口文件为 `main.js`。

3. 保存 `action.yml` 文件。
4. 将修改提交并推送到 `main` 分支：

   ```shell
   git add action.yml
   git commit -m 'create action.yml'
   git pull
   git push
   ```

5. 等待大约 20 秒后刷新本页面。[GitHub Actions](https://docs.github.com/en/actions) 会自动检测更新，并跳转到下一步。