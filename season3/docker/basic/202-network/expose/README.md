# expose

用於 container 跟 container 之間的 port 的溝通，也就是說定義 expose 的 port 號只能被其他 container 存取，不能被 host 也就是外部存取


## 啟動 mysql 作為 server


```
docker run -d \
--name mysql-server \
-e MYSQL_ADMIN_PASS="pass" \
--expose 3306 \
dgraziotin/mysql
```

執行 `docker ps`

將會看到下面結果，可以看到 ports 為 `3306/tcp`

```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
5af9391204b2        dgraziotin/mysql    "/run.sh"           4 seconds ago       Up 3 seconds        3306/tcp            mysql-server
```

## 啟動 mysql 作為 client

```
docker run -it --rm \
--name mysql-client \
--link mysql-server \
dgraziotin/mysql \
mysql -uadmin -h mysql-server -ppass
```

將會看到 mysql 已正確連接

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.5.47-0ubuntu0.14.04.1 (Ubuntu)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```
