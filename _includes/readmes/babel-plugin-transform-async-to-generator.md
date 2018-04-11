# babel-plugin-transform-async-to-generator

> 将 async 函数转为 ES2015 的 generators

## 示例

**输入**

```javascript
async function foo() {
  await bar();
}
```

**输出**

```javascript
var _asyncToGenerator = function (fn) {
  ...
};
var foo = _asyncToGenerator(function* () {
  yield bar();
});
```

## 安装

```sh
npm install --save-dev babel-plugin-transform-async-to-generator
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-async-to-generator"]
}
```

### 通过 CLI

```sh
babel --plugins transform-async-to-generator script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-async-to-generator"]
});
```

## 参考

* [提案：ECMAScript 中的 Async 函数](https://github.com/tc39/ecmascript-asyncawait)
