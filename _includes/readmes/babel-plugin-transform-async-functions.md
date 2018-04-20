# babel-plugin-transform-async-functions

将 async 函数编译为 ES5

## 安装

```sh
npm install --save-dev babel-plugin-transform-async-functions
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
{
  "plugins": ["transform-async-functions"]
}
```

### 通过 CLI

```sh
babel --plugins transform-async-functions script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-async-functions"]
});
```
