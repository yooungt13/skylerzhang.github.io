---
layout: post
title:  "让Apache显示文件列表"
date:   2014-10-18 
categories: apache
tag: apache
---



今天升级OSX10.10 之后localhost 访问本地Apache根目录的时候看不到文件列表

![提示如下图]({{ site.url }}/images/www.jpg)

在网上查找之后发现是Apache配置的问题，解决方法如下

1、 在找到 `/etc/apache2/users/skyler.conf ` 文件打开

2、 文件里又这么一段

    <Directory "/Library/WebServer/Documents">
        
        Options FollowSymLinks 
        
        MultiviewsMatch Any
       
        AllowOverride None
    
        Require all granted
    </Directory>

3、修改成

    <Directory "/Library/WebServer/Documents">
        
        Options Indexes FollowSymLinks
        
        MultiviewsMatch Any
       
        AllowOverride None
    
        Require all granted
    </Directory>

4、重启Apache即可   `Apachectl restart `

