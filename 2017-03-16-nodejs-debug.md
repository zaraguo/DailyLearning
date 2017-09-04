# 调试 node 程序

## console.log / console.trace / console.time

在代码中添加一些调试输出，以便对运行中的情况有所了解。

## debugger

在代码中增加 `debugger;` 然后用 `node debug index.js` 启动，就可以进入调试模式。程序将会执行到 `debugger;` 处中断，以便你打印上下文变量。

| 值            | 解释                                       |
|---------------|--------------------------------------------|
| repl          | 在当前上下文打印求值                       |
| run           | 执行脚本                                   |
| restart       | 重新执行脚本                               |
| cont/c        | 继续执行，直到遇到下一个断点或是执行到结束 |
| next/n        | 单步执行                                   |
| step/s        | 单步执行，并进入函数                       |
| out/o         | 从函数中出来                               |
| backtree/bt   | 打印当前调用堆栈                           |
| watch(expr)   | 把表达式 expr 加入监视列表                 |
| unwatch(expr) | 把表达式 expr 从监视列表移除               |
| watchers      | 显示监视列表中所有的表达式和值             |
| list(5)	     | 显示当前执行到的前后5行代码                |

## node --inspect

在 node v6.3.0 及以上支持。
当你用 node 运行时增加 `--inspect` 将返回一个 url 用于在 Chrome 中调试本地 node 程序，你可以增加断点，打印变量，单步执行等等。同时你在浏览器中对文件的修改保存将被热加载，而不需要中断后端的 node 进程。

![](/media/14896688871017.jpg)


## node-inspector 等第三方工具

类似上面的 `--inspect`，具体详见 [README](https://github.com/node-inspector/node-inspector#quick-start)

## 关于 js 内存泄露的调试

 [heapdump] + [devtools]

# 参考
[node-debug tutorial](http://i5ting.github.io/node-debug-tutorial/)
[DevTools in 2016: Accelerate your workflow - Google I/O 2016](https://www.youtube.com/watch?v=x8u0n4dT-WI&feature=youtu.be&t=2571)
[如何分析 Node.js 中的内存泄漏](https://zhuanlan.zhihu.com/p/25736931)
[heapdump]: https://github.com/bnoordhuis/node-heapdump
[devtools]: https://github.com/Jam3/devtool


