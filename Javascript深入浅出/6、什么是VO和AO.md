在JavaScript中，VO（Variable Object）是指变量对象，而 AO（Activation Object）是指激活对象。它们在不同的执行上下文中扮演着类似的角色，用于存储变量和函数的声明。

VO 和 AO 是执行上下文的内部数据结构，用于维护当前上下文中定义的变量和函数。它们是在创建执行上下文时被创建的，并在执行过程中被用来解析标识符（Identifier Resolution）。

VO 和 AO 存储的内容包括：

1. 变量声明：包括通过 `var`、`let`、`const` 声明的变量。
1. 函数声明：包括函数声明和函数表达式（通过 `function` 关键字定义的函数）。

在函数执行的过程中，VO 或 AO 会被用来解析变量和函数的标识符。当访问一个变量时，JavaScript 引擎会在 VO 或 AO 中查找该变量的值。如果在当前上下文的 VO 或 AO 中找不到，则会继续沿着作用域链向上查找。

需要注意的是，VO 和 AO 的名称和具体实现在不同的 JavaScript 引擎中可能会有所不同。在早期的 JavaScript 实现中，VO 更常见，而在现代 JavaScript 引擎中，AO 或 Lexical Environment 更常见。

以下是一个简单的示例，展示了 VO 和 AO 的概念：

```javascript
function foo() {
  var x = 10;
  console.log(x);
}

foo();
```

在上述示例中，当执行 `foo()` 时，会创建 `foo` 函数的执行上下文，并创建相应的 VO 或 AO。在 `foo` 函数内部，变量 `x` 被声明为 `10`，并存储在 VO 或 AO 中。当调用 `console.log(x)` 时，JavaScript 引擎会在 VO 或 AO 中查找变量 `x` 的值，并输出 `10`。

VO 和 AO 是 JavaScript 执行上下文中的重要概念，用于管理变量和函数的声明。它们通过解析标识符的方式，帮助 JavaScript 引擎确定变量和函数在执行过程中的访问规则。