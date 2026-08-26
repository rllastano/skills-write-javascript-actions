<!--
  <<< Author notes: Step 5 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 5: 在 workflow 文件中引用你的 Action

_干得漂亮! :tada:_

接下来的步骤会把你刚创建的 Action 添加到仓库中已有的工作流文件 [`my-workflow.yml`](/.github/workflows/my-workflow.yml) 中。

### :keyboard: 实操环节: 在 workflow 文件中引用自定义 Action

在 `my-workflow.yml` 文件中添加如下内容：

```yaml
- name: ha-ha
  uses: ./.github/actions/joke-action
```

完整的 workflow 文件示例如下：

```yaml
name: JS Actions

on:
  issues:
    types: [labeled]

jobs:
  action:
    if: ${{ !github.event.repository.is_template }}
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - name: ha-ha
        uses: ./.github/actions/joke-action
```

说明：

* 我们这里使用 `issues` 事件触发，而不是 `pull_request`。
* 移除了之前示例中的 `hello-world` Action。
* `uses: ./.github/actions/joke-action` 指向本地的自定义 Action 目录。

你可以在浏览器中打开 [`my-workflow.yml`](/.github/workflows/my-workflow.yml) 并直接[编辑文件](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files)。
记得选择 **Commit directly to the main branch** 以直接提交更改。

等待大约 20 秒后刷新本页面，[GitHub Actions](https://docs.github.com/en/actions) 会自动检测更新，并进入下一步。