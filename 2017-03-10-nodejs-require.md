# nodejs 中的几种不采用相对路径 require 的方式

## 前言
当 nodejs 项目比较复杂时，require 的相对路径将十分复杂和丑陋，那么有哪些不错的取代方式来进行比较优雅的 require 呢？

## require 的查找规则

1. 内置模块，直接返回
2. 如果包含路径
    1. 根据相对父模块的相对路径，确定绝对路径。
    2. 将其作为文件依次查找, x、x.js、x.json、x.node 
    3. 将其作为目录依次查找, x/package.json、x/index.js、x/index.json、x/index.node 
3. 如果不包含路径，依次向上寻找可能的 node_modules 目录, 依次进行 step 2 下的步骤

## require hack

### 软连接

将你所需要的模块 link 到 node_modules 文件夹下，hack step 3。

```
#!/bin/bash

TARGET_DIR=node_modules

ln -sf ./models $TARGET_DIR/
```

那么你可以像这样引用你的模块了

```
var User = require('models/user');
```

### 使用绝对路径访问

在 global 变量中记录项目的绝对路径, no hack。

```
global.__base = __dirname + '/';
var User = require(__base + 'models/user');
```

### NODE_PATH

利用 NODE_PATH 可以将你的 baseDir 放入项目模块的 modulePaths 中，hack step3。

```
export NODE_PATH=.
NODE_PATH=. node app
```

### 使用第三方模块解决

#### node-module-app/rfr

```
// require 中的路径都是根据 baseDir 的相对路径
require('app-module-path').addPath(baseDir);
var User = require('models/user');
```

## 参考
[Better local require() paths for Node.js](https://gist.github.com/branneman/8048520#comment-1412502)
[require() 源码解读](http://www.ruanyifeng.com/blog/2015/05/require.html)
