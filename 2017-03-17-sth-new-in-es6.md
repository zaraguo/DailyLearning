# ES6 的一些变化
## ES6 中函数本身的作用域只存在所在的块级作用于之内

```
function foo() { console.log('outside the block'); }
if (true) {
    function foo() { console.log('inside the block'); }
}
foo();
```

```
'inside the block'  // ES5
'outside the block' // ES6
```

## ES6 箭头函数内的 this 变量将捕获所在上下文的 this 值，在词法层面已经完成了绑定

```
var obj = {
    base: 1,
    a: () => this.base,
    b: function () {
        return this.base
    }
}
obj.a(); //undefined
obj.b(); //1
```
