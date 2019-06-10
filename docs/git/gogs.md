# Gogs安装

#### 创建目录
```
$ mkdir /data/docker/gogs
```

#### 编写docker-compose文件
```
$ cd /data/docker/gogs
$ vim docker-compose.yml
```
添加以下内容
net-mysql 是否需要 再确定,应该不需要
```
version: "3"
services:
  gogs:
    image: gogs/gogs
    container_name: host_gogs
    hostname: host_gogs
    ports:
      - "10022:22"
      - "10080:3000"
    volumes:
      - /data/gogs:/data
    networks:
     - net-gogs
     - net-mysql
networks:
  net-gogs:
  net-mysql:
```
#### 启动
```
docker-compose up -d
```

#### nginx返向代理配置
```
upstream gogs {
 server 内网地址:10080; #注:配置docker服务器时，这里的内网地址不可以是127.0.0.1
}

server{
    listen 80;
    server_name gogs.abc.com;
    error_log  /var/log/dnmp/gogs.error.log  warn;
    access_log  /var/log/dnmp/gogs.access.log  main;

    location / {
        proxy_pass   http://gogs;
        proxy_set_header Host $host;
        proxy_set_header X-Real_IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

#### 重启nginx
#### 远端访问 gogs.abc.com

至此gogs安装完成 



### 错误处理

502

```
2019/06/10 09:53:00 [error] 6#6: *1 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: 1.119.196.210, server: gogs.abc.com, request: "GET / HTTP/1.1", upstream: "http://ip:10080/", host: "gogs.iutree.com"
2019/06/10 09:53:00 [error] 6#6: *1 recv() failed (104: Connection reset by peer) while reading response header from upstream, client: 1.119.196.210, server: gogs.abc.com, request: "GET /favicon.ico HTTP/1.1", upstream: "http://ip:10080/favicon.ico", host:
 "gogs.abc.com", referrer: "http://gogs.abc.com/"
```
 



























