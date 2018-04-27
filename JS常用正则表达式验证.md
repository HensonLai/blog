## 手机号码验证

``` js
var phone = /^1[3|4|5|8][0-9]\d{4,8}$/;
phone.test("待验证的手机号");
```

## 姓名验证
``` js
var realname = /^[\u4E00-\u9FA5A-Za-z]+$/;
realname.test("待验证人姓名");
```