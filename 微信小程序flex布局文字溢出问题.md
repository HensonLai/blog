## 问题描述
在浏览器中对于css语法：
```css
    overflow: hidden;
    text-overflow: ellipsis;
    white-sapce: no-wrap;
```

对于文字溢出会用“...”来表示，但在微信小程序中，溢出文本不但不会省略，而且还会撑大宽度。解决的办法有两个：
    1.就是固定其宽度，毕竟在小程序是在手机端打开的，屏幕的大小也不尽相同，这就远离我们用flex布局的初衷了
    2.就是在对于其父级添加如下样式
``` css
    overflow: auto;
```

## 举个例子
wxml 代码如下：
``` html
<view class='test'>
    <view class='v1'>我希望当这段文字内容过长的时候在能够对于超出的文本进行隐藏，并用“...”表示，而且不会破坏布局</view>
    <view class='v2'>Hi</view>
</view>

```
wxss 代码如下：

``` css
.test {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    aline-items: center;
    
    overflow: auto;      /*加上这句话*/
}
.v1 {
    flex: 1;
    white-space: no-wrap;
    text-overflow: ellipsis;
    overflow: hidden;
}
```


