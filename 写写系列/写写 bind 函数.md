## 分析

`bind` 方法返回一个新的函数，在新的函数被调用时，这个新的函数的 `this` 被指定为 `bind` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。

这样看来，被 `bind` 函数返回的新函数除了调用时的 `this` 指向有改变，其他地方没有任何不同。返回的内容也要和原来的一样。

## 代码

1. 改变 `this` 指向
2. 第一个参数是 `this` 的值，后面的参数是 **函数接受的参数** 的值
3. 返回值不变

```JavaScript
Function.prototype.myBind = function () {
  const self = this
  // 将类组数对象 arguments 转换为组数
  const args = [...arguments]
  // 取出要绑定的 this 对象保存
  // 并将 this 对象从 args 中移除
  // 以便后面直接当做参数传递
  const _this = args.shift()

  // 返回一个新函数
  return function () {
    // 返回值不变
    self.apply(_this, args)
  }
}
```
