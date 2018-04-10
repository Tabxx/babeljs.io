# babel-plugin-transform-async-to-module-method

> 将 async 函数转换为 Bluebird 协同程序

## 示例

**输入**

```javascript
async function foo() {
  await bar();
}
```

**输出**

```javascript
var Bluebird = require("bluebird");

var foo = Bluebird.coroutine(function* () {
  yield bar();
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-async-to-module-method
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

未包含选项：

```json
{
  "plugins": ["transform-async-to-module-method"]
}
```

包含选项：

```json
{
  "plugins": [
    ["transform-async-to-module-method", {
      "module": "bluebird",
      "method": "coroutine"
    }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-async-to-module-method script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-async-to-module-method"]
});
```
