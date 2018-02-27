### nginx的安装

下载地址：[nginx官网](http://nginx.org/)

下载到软件包后，解压 nginx-nginx1.13.7.zip 包到你喜欢的根目录，并将目录名改为nginx

### nginx的命令操作

1. 启动nginx

```
start nginx
```

打开任务管理器，查看 nginx.exe 进程，有二个进程会显示，占用系统资源相当少。然后再打开浏览器，输入 [http://127.0.0.1/](http://127.0.0.1/)  就可以看到nginx的欢迎页面	

2. 停止nginx

```
nginx -s stop
```

3. 重新加载配置文件

```
nginx -s reload
```

4. 退出nginx

```
nginx -s quit
```

### nginx的配置



### 反向代理

```javascript
#proxy config
location /douban {
    rewrite ^.+/douban/?(.*)$ /$1 break;
    proxy_pass http://api.douban.com/v2/movie;
}
```

1. `/douban`

是一个匹配规则，用于拦截请求，匹配任何以 /api开头的地址，匹配符合以后，停止往下搜索正则

2. `rewrite ^.+/douban/?(.*)$ /$1 break;`

重写拦截进来的请求，并且只能对域名后边的除去传递的参数外的字符串起作用

3. `proxy_pass`

把请求代理到其他主机

### 虚拟主机

在http中新增server

```javascript
#VirtuaHost
server {
    listen 80;
    server_name jindong.com;
    index index.html index.htm index.php;
    root html/jd/;
}
```

