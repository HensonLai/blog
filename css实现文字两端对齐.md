文本两端对齐：

``` css
.text {
    width: 200px;
    text-align: justify;
}
.text::after {
    content: '';
    padding-left: 100%;
    display: inline-block;
}
```