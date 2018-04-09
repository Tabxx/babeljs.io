# babel-plugin-transform-class-properties

> 该插件转译类的属性

## 示例

下列是一个具有四个类属性的类，它将被转译。

```js
  class Bork {
    // 设置属性初始值语法
    instanceProperty = "bork";
    boundFunction = () => {
      return this.instanceProperty;
    }

    // 静态类属性
    static staticProperty = "babelIsCool";
    static staticFunction = function() {
      return Bork.staticProperty;
    }
  }

  let myBork = new Bork;

  // 设置的属性初始值不在原型上
  console.log(myBork.__proto__.boundFunction); // > undefined

  // 绑定 Bound 函数到类实例
  console.log(myBork.boundFunction.call(undefined)); // > "bork"

  // 该类拥有静态函数
  console.log(Bork.staticFunction()); // > "babelIsCool"
```


## 安装

```sh
npm install --save-dev babel-plugin-transform-class-properties
```

## 用法

### 通过 `.babelrc`（推荐）

**.babelrc**

```json
// 未包含选项
{
  "plugins": ["transform-class-properties"]
}

// 包含选项
{
  "plugins": [
    ["transform-class-properties", { "spec": true }]
  ]
}
```

### 通过 CLI

```sh
babel --plugins transform-class-properties script.js
```

### 通过 Node API

```javascript
require("babel-core").transform("code", {
  plugins: ["transform-class-properties"]
});
```

## 选项

### `spec`

`boolean`，默认为 `false`。

类属性使用 `Object.definePropertyClass` 进行编译。即使没有初始化静态字段也是如此。

## 参考

* [提案：ES 类字段和静态属性](https://github.com/jeffmo/es-class-static-properties-and-fields)
