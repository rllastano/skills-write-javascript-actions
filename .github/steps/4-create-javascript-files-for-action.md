<!--
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 4: 为你的 Action 编写 JavaScript 代码

_元数据文件已经加好了！ :dancer:_

## 文件结构

在 JavaScript（以及其他编程语言）中，我们通常会把代码拆分成多个模块，方便阅读和维护。
由于 JavaScript Actions 本质上也是一段根据特定触发条件运行的 JS 程序，我们同样可以采用模块化的方式组织代码。

在本步骤中，我们将创建两个文件：

1. **`joke.js`**：负责从外部 API 获取一个笑话；
2. **`main.js`**：调用上面的模块，并将笑话输出到控制台。

在下一步中，我们还会进一步扩展它的功能。

### 获取笑话数据

**笑话 API**

我们首先创建 `joke.js` 文件，用来从 [icanhazdadjoke API](https://icanhazdadjoke.com/api) 获取笑话。
这个 API 不需要认证，但需要在请求头中设置一些参数。

调用该 API 后，我们会收到一个 JSON 对象，格式如下：

```json
{
  "id": "0LuXvkq4Muc",
  "joke": "I knew I shouldn't steal a mixer from work, but it was a whisk I was willing to take.",
  "status": 200
}
```

返回的数据包含三个键值对，其中我们只关心 `joke` 字段，它就是笑话的内容。

**笑话模块实现**

在 `.github/actions/joke-action` 目录下创建文件 `joke.js`，内容如下：

```javascript
const request = require("request-promise");

const options = {
  method: "GET",
  uri: "https://icanhazdadjoke.com/",
  headers: {
    Accept: "application/json",
    "User-Agent": "Writing JavaScript action GitHub Skills course.",
  },
  json: true,
};

async function getJoke() {
  const res = await request(options);
  return res.joke;
}

module.exports = getJoke;
```

**代码说明：**

* 首先导入我们之前通过 `npm` 安装的 `request-promise` 库；
* 定义 `options` 对象，其中包含请求方式、目标 URL 以及请求头；

   * `Accept` 表示希望返回 JSON 格式；
   * `User-Agent` 是 API 要求的标识；
* 定义一个异步函数 `getJoke()`，发送请求并获取响应；
* 函数返回 JSON 对象中的 `joke` 字段内容（每次调用都会返回不同的笑话）；
* 最后通过 `module.exports` 导出函数，以便在 `main.js` 中使用。

### 创建 Action 的主入口

**Main 模块**

在同一目录下创建 `main.js` 文件，内容如下：

```javascript
const getJoke = require("./joke");
const core = require("@actions/core");

async function run() {
  const joke = await getJoke();
  console.log(joke);
  core.setOutput("joke-output", joke);
}

run();
```

**代码说明：**

* 首先引入我们自己写的 `joke.js` 模块，以及 GitHub 提供的 `@actions/core` 库；
* 定义一个异步函数 `run()`：

   * 调用 `getJoke()` 获取笑话内容并存入变量 `joke`；
   * 将笑话打印到控制台；
   * 使用 `core.setOutput()` 将笑话内容设置为输出参数 `joke-output`（稍后会被其他步骤使用）。
* 最后调用 `run()` 来执行整个流程。

### :keyboard: 实操环节

1. 创建文件 `.github/actions/joke-action/joke.js`，内容如下：

   ```javascript
   const request = require("request-promise");

   const options = {
     method: "GET",
     uri: "https://icanhazdadjoke.com/",
     headers: {
       Accept: "application/json",
       "User-Agent": "Writing JavaScript action GitHub Skills course.",
     },
     json: true,
   };

   async function getJoke() {
     const res = await request(options);
     return res.joke;
   }

   module.exports = getJoke;
   ```

2. 保存 `joke.js` 文件。
3. 创建文件 `.github/actions/joke-action/main.js`，内容如下：

   ```javascript
   const getJoke = require("./joke");
   const core = require("@actions/core");

   async function run() {
     const joke = await getJoke();
     console.log(joke);
     core.setOutput("joke-output", joke);
   }

   run();
   ```

4. 保存 `main.js` 文件。
5. 提交修改并推送到 GitHub：

   ```shell
   git add joke.js main.js
   git commit -m 'creating joke.js and main.js'
   git pull
   git push
   ```

6. 等待大约 20 秒后刷新本页面。[GitHub Actions](https://docs.github.com/en/actions) 会自动检测更新，并进入下一步。