# vim 禁用方向键

由于鄙人之前在 vim 下有些移动操作还是会卑劣地使用方向键，遭到了某人的抨击，故禁用之。

```
map <Left> <Nop>
map <Right> <Nop>
map <Up> <Nop>
map <Down> <Nop>
```

---- 
#### 更新

只有以上的配置会使得在插入模式下方向键仍可用，因为 map 只针对普通模式和可视模式下作了映射，故添加：

```
imap <Left> <Nop>
imap <Right> <Nop>
imap <Up> <Nop>
imap <Down> <Nop>
```

酱紫在插入模式下方向键也被禁用啦\~

`1491 days left`
