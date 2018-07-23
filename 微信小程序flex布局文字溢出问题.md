## 问题描述
在浏览器中对于css语法：
```css
    overflow: hidden;
    text-overflow: ellipsis;
    white-sapce: no-wrap;
```

对于文字溢出会用“...”来表示，但在微信小程序中，溢出文本不但不会省略，而且还会撑大宽度。解决的办法就是在对于其父级添加
``` css
    overflow: auto;
```
