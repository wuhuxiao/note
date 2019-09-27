# Docker搭建个人wordpress网站

## Getting Super Powers

拉取镜像mariadb和wordpress镜像

```
docker pull wordpress
docker pull mariadb
```

启动数据库服务

```text
 docker run --name wp-db -e MYSQL_ROOT_PASSWORD=123456 -d mariadb
```

说明：--name后面是容器的名称，MYSQL\_ROOT\_PASSWORD=123456为数据库用户root的密码为123456，-d表示此数据库容器后台运行，mariadb表示镜像

启动wordpress服务

```text
docker run --name mywordpress --link wp-db:mysql -p 8001:80 -d wordpress
```

说明：--link为数据库关联，注意此处wp-db后为mysql不是mariadb ，-p表示端口映射

打开IP:8081网址，语言选择香港，即可进入注册安装。

