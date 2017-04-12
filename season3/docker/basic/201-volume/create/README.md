# docker volume create and inspect


## create

```
Usage:	docker volume create [OPTIONS]

Create a volume

  -d, --driver=local    Specify volume driver name
  --help                Print usage
  --label=[]            Set metadata for a volume
  --name                Specify volume name
  -o, --opt=map[]       Set driver specific options
```

### 建立第一個 volume

`docker volume create --name mysql-data`

建立完成後我們可以透過 inspect 來確認 host 的檔案位置


## inspect

```
Usage:	docker inspect [OPTIONS] CONTAINER|IMAGE [CONTAINER|IMAGE...]

Return low-level information on a container or image

  -f, --format       Format the output using the given go template
  --help             Print usage
  -s, --size         Display total file sizes if the type is container
  --type             Return JSON for specified type, (e.g image or container)

```

執行 `docker volume inspect mysql-data`

將會看到下列輸出

```
[
    {
        "Name": "mysql-data",
        "Driver": "local",
        "Mountpoint": "/var/lib/docker/volumes/mysql-data/_data",
        "Labels": {}
    }
]
```

就可以直接透過 host 的 filesystem 進行存取


## 執行 mysql docker


```
docker run -d -p "3306:3306" \
-e MYSQL_ADMIN_PASS="pass" \
-e MYSQL_USER_DB="testdb" \
-e CREATE_MYSQL_BASIC_USER_AND_DB=true \
-v mysql-data:/var/lib/mysql/ \
dgraziotin/mysql
```

接著我們可以執行 `sudo ls /var/lib/docker/volumes/mysql-data/_data`

可以看到 db 資料已產出在 host 對應的 folder

```
ib_logfile0  ib_logfile1  ibdata1  mysql  performance_schema  testdb
```
