ThinkPHP5的一些小问题：模板文件中使用未定义变量报错，隐藏url 中的 index.php 使用PATH_INFO模式，ThinkPHP5 框架目录下的.gitignore文件，输出二维码图片乱码

<!-- more -->
## 模板文件使用未定义变量报错
模板文件使用未定义变量报错，解决方法就是在application/config.php 第一行添加一句话
``` php
<?php
    ……
    error_reporting(E_ERROR | E_WARNING | E_PARSE); **（要添加的）**
    return [
        ...
        ...
    ];
```

## 隐藏url 中的 index.php 使用PATH_INFO模式
ThinkPHP5默认的 public/.htaccess 文件是这样的：
``` php
<IfModule mod_rewrite.c>
  Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
</IfModule>
```
需要修改成下面这样：
``` php
<IfModule mod_rewrite.c>
  Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  #RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]
  RewriteRule ^(.*)$ index.php [L,E=PATH_INFO:$1] **（这个是添加的）**
</IfModule>
```

## ThinkPHP5 框架目录下的.gitignore文件
在ThinkPHP5框架中默认很多的目录下都有 .gitignore 文件，而且文件里面都有让git忽略当前目录下的某些文件。这就很坑了，如果你没有删除这些文件，当你使用git版本管理的时候，很多目录下的文件都没有提交到仓库中。
所以当我们初次使用ThinkPHP5框架的时候，首先就要把所有的.gitignore文件删除，然后再自定义自己的.gitignore（随你）。
那删除文件怎么删呢，这么多的目录，难道我一个一个目录展开然后删除？windows用户打开git bash 命令窗口，并进入项目所在目录，然后操作，请看下面代码：
``` bash
find . -name ".gitignore" | xargs rm -rf
# find 查找命令
# . 当前目录下
# -name 文件名查找
# xargs rm -rf 查找后执行删除命令
```

## ThinkPHP5 输出二维码图片乱码
在返回图片的控制中加入下面这行
``` php
return response("", 200)->contentType("image/png");
```