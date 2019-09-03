# Docker使用Nginx代理转发SSR

SSR由于使用的是国外的VPS的ip，会有很大几率被国内网络屏蔽，例如本人自搭的SSR在家里使用电信网络没问题，到公司后使用移动网络被屏蔽。

解决方法之一就是使用华为云等国内服务器进行代理转发，本文介绍的是使用docker进行Nginx代理转发。

nginx配置文件

```
user  root;
worker_processes  1;

events {
    worker_connections  1024;
}

stream {

    upstream group1 {
        hash $remote_addr consistent;
        server 108.61.XXX.XXX:2333;     # ip:port
    }

    server {
        listen 2333;
        listen 2333 udp;
        proxy_pass group1;
    }

}
```

docker-compose.yml文件

```
version: '2'
services:
  nginx_lb:
    image: nginx:latest
    ports:
     - "2333:2333"
     - "2333:2333/udp"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
```

 使用docker-compose启动nginx

```text
docker-compose up -d
```

启动配置SSR连接,用国内服务器的公网ip替换vps的ip，如图

![](../.gitbook/assets/image%20%288%29.png)

