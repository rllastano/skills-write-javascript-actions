<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 3: Action 元数据文件

在上一步中我们已经创建好了 Action 元数据文件，本节我们来完善它。

## 关于 Action 的元数据

每个 GitHub Action 都必须具有一个 **元数据文件（metadata file）**。并遵守如下规则：

- 文件名**必须**为 `action.yml`.
- 无论是 Docker 类型还是 JavaScript 类型的 Action 都需要它。
- 文件内容使用 **YAML** 语法编写。

这个文件主要定义了 Action 的以下信息：

| 参数              | 说明                                                                | 是否必需 |
| ---------------- | ------------------------------------------------------------------- | :--: |
| **Name**        | Action 的名称，用于在工作流中直观识别。                                    |   ✅  |
| **Description** | 对 Action 功能的简要描述。                                               |   ✅  |
| **Inputs**      | 输入参数，允许你在运行时向 Action 传入数据。这些参数在运行器中会作为环境变量使用。 |   ❌  |
| **Outputs**     | 指定 Action 执行后产生的输出数据，供工作流中后续的步骤使用。                  |   ❌  |
| **Runs**        | Action 执行时要运行的命令或入口文件。                                      |   ✅  |
| **Branding**    | 可设置图标和颜色，在 GitHub Marketplace 中个性化展示你的 Action。           |   ❌  |

---

想了解更多，请查看 [Action 元数据语法说明](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/metadata-syntax-for-github-actions)

### :keyboard: 实操环节：补充元数据文件

以下步骤都在 `.github/actions/joke-action` 目录下完成。

我们的 Action 不需要复杂的元数据即可运行。本次我们不会接收任何输入参数，但会定义一个输出参数。

1. 更新元数据文件 `.github/actions/joke-action/action.yml`，内容如下：

   ```yaml
   name: "my joke action"

   description: "use an external API to retrieve and display a joke"

   outputs:
     joke-output:
       description: The resulting joke from the icanhazdadjokes API

   runs:
     using: "node16"
     main: "main.js"
   ```

2. 保存 `action.yml` 文件。
3. 提交并推送修改到 GitHub：

   ```shell
   git add action.yml
   git pull   
   git commit -m 'add metadata for the joke action'
   git push
   ```
4. 等待大约 20 秒后刷新本页面，[GitHub Actions](https://docs.github.com/en/actions) 会自动检测更改并进入下一步。