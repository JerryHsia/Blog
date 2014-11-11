---
author: Jerry Hsia
title: Nginx反向代理和负载均衡初步
excerpt:
layout: post
views:
  - 100
category:
  - other
tags:
  - Linux
post_format: [ ]
---
反向代理，从192.168.160.100:8080获取php的请求
{% highlight bash %}
location ~ \.php$ {
    proxy_pass 192.168.160.100:8080;
}
{% endhighlight %}
负载均衡，在http模块中加入
{% highlight bash %}
upstream server_group {
   server 192.168.160.100:8080;
   server 192.168.160.101:8080;
}
#以上实现两台服务器均衡，如果要分配权重，可如下配置
upstream server_group {
   server 192.168.160.100:8080 weight=1 max_fails=2 fail_timeout=30s;
   server 192.168.160.101:8080 weight=1 max_fails=2 fail_timeout=30s;
}
#两次无响应则将服务器踢出
{% endhighlight %}
在server中加入
{% highlight bash %}
location ~ \.php$ {
    proxy_pass http://server_group; #这里的名字和上面的server_group的名字相同
    proxy_redirect off;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
}
{% endhighlight %}