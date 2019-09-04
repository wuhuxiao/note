# Nginx

Nginx解析，转发，代理

服务器解析域名

Nginx目录下有nginx.conf文件里面是nginx的配置，其中的include /etc/nginx/conf.d/\*.conf;  是将conf.d的目录下的配置文件.conf 导入到总的配置中

简单的域名解析如下

```text
server {
  listen 80;//监听80端口
  server_name wwww.whuwhx.top;//监听域名解析
  
  location / {
    proxy_pass http://127.0.0.1:8001;//代理到本机的8001端口
  }

}

```

|  |  |
| :--- | :--- |
| 名称  | 命令  |
| 启动nginx | start nginx |
| 修改配置后重新加载生效 | nginx -s reload  |
|  重新打开日志文件 | nginx -s reopen  |
| 测试nginx配置文件是否正确 | nnginx -t -c nginx.conf |
| 关闭nginx ：快速停止 | nginx nginx -s stop |
| 完整有序的停止 | nginx nginx -s quit  |



