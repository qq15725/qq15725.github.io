I may be slow to respond.

- [Yh5](https://github.com/qq15725/yh5).
- [ddoc](https://github.com/qq15725/ddoc).
- [venomancer](https://github.com/qq15725/venomancer).

- 原型 / 原型链
- 闭包（closure）
  - MDN 对闭包的定义
    > 闭包是指那些能够访问自由变量的函数
  - 自由变量是什么
    > 自由变量是指在函数中使用的，但既不是函数参数也不是函数的局部变量的变量。
  - ECMAScript中，闭包指的是：
    1 从理论角度：所有的函数。因为它们都在创建的时候就将上层上下文的数据保存起来了。哪怕是简单的全局变量也是如此，因为函数中访问全局变量就相当于是在访问自由变量，这个时候使用最外层的作用域。
    2 从实践角度：以下函数才算是闭包：
      即使创建它的上下文已经销毁，它仍然存在（比如，内部函数从父函数中返回）
      在代码中引用了自由变量
  - 实践角度闭包的白话解释
    > 父函数执行后返回存在引用父函数变量的子函数，这个子函数就构成了闭包。
  - 例子
    ```javascript
      function a () {
        var name = 'a'
        return function b () {
          console.log(name)
        }
      }
      var b = a()
      b()
      // 打印 a 
    ```
- setTimeout / setInterval
  - 其回调函数 this 会指向全局环境
  - 运行机制：代码将添加在 Event Loop 队列的队尾中，则实际调用时间 Math.max(所有同步任务执行时间, 定时时间)
  - 根据其运行机制在单线程的 JS 中可以通过 setTimeout(code, 0) 获得最后执行 code 的效果
