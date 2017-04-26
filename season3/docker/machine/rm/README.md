docker-machine 移除
===================

docker-machine 可以建立，當然也可以移除，同樣的我們先建立一 docker-machine

`docker-machine create -d virtualbox test`

查詢 docker-machine 狀態

```
➜  ~ docker-machine ls
NAME       ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
test        *        virtualbox   Running   tcp://192.168.99.100:2376           v1.10.3
```

進行 docker-machine 刪除

`docker-machine rm test`

執行結果如下

```
About to remove test
Are you sure? (y/n): Y
Successfully removed test
```
