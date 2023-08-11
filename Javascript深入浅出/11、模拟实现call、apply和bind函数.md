下面是模拟实现 `call`、`apply` 和 `bind` 函数的示例：

```javascript
// 模拟实现 call 函数
Function.prototype.myCall = function (context, ...args) {
  context = context || window;
  const fnSymbol = Symbol('fn');
  context[fnSymbol] = this;
  const result = context[fnSymbol](...args);
  delete context[fnSymbol];
  return result;
};

// 模拟实现 apply 函数
Function.prototype.myApply = function (context, args) {
  context = context || window;
  const fnSymbol = Symbol('fn');
  context[fnSymbol] = this;
  let result;
  if (args && Array.isArray(args)) {
    result = context[fnSymbol](...args);
  } else {
    result = context[fnSymbol]();
  }
  delete context[fnSymbol];
  return result;
};

// 模拟实现 bind 函数
Function.prototype.myBind = function (context, ...args) {
  const self = this;
  return function (...innerArgs) {
    return self.apply(context, args.concat(innerArgs));
  };
};
```

上述代码通过给 `Function.prototype` 添加 `myCall`、`myApply` 和 `myBind` 方法，实现了对应的模拟函数。

- `myCall` 方法模拟了 `call` 函数的行为。它将函数作为对象的方法调用，并将 `this` 绑定到传入的 `context` 上。

- `myApply` 方法模拟了 `apply` 函数的行为。它也将函数作为对象的方法调用，并将 `this` 绑定到传入的 `context` 上。不同之处在于，`myApply` 接受一个数组作为参数。

- `myBind` 方法模拟了 `bind` 函数的行为。它返回一个新的函数，新函数会在调用时将 `this` 绑定到传入的 `context` 上，并接受一组参数。注意，`myBind` 返回的函数可以作为构造函数使用，保留原函数的原型链。

需要注意的是，上述实现只是简单的模拟，并没有考虑一些边界情况，例如原函数是否是箭头函数、是否可以被 `new` 调用等。在实际使用中，建议使用原生的 `call`、`apply` 和 `bind` 函数，它们已经被广泛测试和使用，并具备更好的兼容性和性能。