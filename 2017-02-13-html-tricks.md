# html tricks

## 页面元素修改

如果要用脚本更改一个页面元素的多个属性，可以 clone 一个元素进行修改，再用修改后的元素替换原先的元素。这样可以避免页面的多次渲染，但是 clone 元素会丢失老元素绑定的监听事件。

```
// Efficiently manipulating a node by cloning it

var element = document.querySelector(".my-node");
var elementClone = element.cloneNode(true); // (true) clones child nodes too, (false) doesn't

elementClone.textContent = "I've been manipulated...";
elementClone.children[0].textContent = "...efficiently!";
elementClone.style.backgroundColor = "green";

element.parentNode.replaceChild(elementClone, element);
```

## window.onload vs. document.onload

window.onload 所有页面 Dom 元素 images links sub-frames 被加载完成后被执行

document.onload 所有页面 Dom 元素被加载完执行，可能优先于图片及其他内容

## async vs. defer

async 脚本的加载和执行与页面的加载和渲染并行执行，执行顺序为某个脚本加载完便执行

defer 脚本的加载与页面的加载和渲染并行执行，脚本的执行发生在页面元素解析完成之后，DOMContentLoaded 事件触发之前。执行顺序为加载顺序。

## css media

```
// On mobile this css will download in the background and not disrupt the page load.
<link rel="stylesheet" href="desktop-styles.css" media="min-width: 590px">
```
