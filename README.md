# RUN DUMP 基于 docker 搭建的一键安装环境

使用时请修改 `.env` 文件

```sh
$ cp .env.exp .env
```

目录结构

```text

├── docker-compose.yml
├── hosts       ---- 项目目录
├── log         ---- 日志目录
└── service     ---- 服务目录
    ├── mysql
    │   ├── conf.d  --- mysql 配置文件
    │   │   └── mysql.cnf
    │   └── databases   --- 数据库目录
    ├── nginx
    │   ├── conf.d     ---- web配置目录
    │   │   └── default.conf
    │   ├── fastcgi_params
    │   └── nginx.conf
    ├── php
    │   ├── Dockerfile
    │   └── php.ini
    └── redis
        ├── data    ---- redis 数据目录
        └── redis.conf

```


