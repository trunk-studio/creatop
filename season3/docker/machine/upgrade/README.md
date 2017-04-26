docker-machine 升級
===================

Docker 目前處在快速發展的當下，其版本更新非常快速，很多新特性也一直不停的推陳出新，很多時候我們要進行升級時，需要連線到 host 主機才能進行，但假設一開始就用 docker-machine 在進行 Docker Host 的管理，我們將可以很方便的進行升級。

假設我們已經有兩台 docker host 透過 ls 查出下面資訊

```
➜  ~ docker-machine ls
NAME       ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
dev        *        virtualbox   Running   tcp://192.168.99.100:2376           v1.10.2
test       -        virtualbox   Running   tcp://192.168.99.101:2376           v1.10.3
```

可以看到其中 dev 是屬於較舊的版本，我們將可以透過下面指令進行更新

`docker-machine upgrade dev`

將會看到下面訊息的輸出

```
Waiting for SSH to be available...
Detecting the provisioner...
Upgrading docker...
Stopping machine to do the upgrade...
Upgrading machine "dev"...
Copying /Users/spooky/.docker/machine/cache/boot2docker.iso to /Users/spooky/.docker/machine/machines/dev/boot2docker.iso...
Starting machine back up...
(dev) Check network to re-create if needed...
(dev) Waiting for an IP...
Restarting docker...
```

再次查詢 docker-machine 狀態

```
➜  ~ docker-machine ls
NAME       ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
dev        *        virtualbox   Running   tcp://192.168.99.100:2376           v1.10.3
test       -        virtualbox   Running   tcp://192.168.99.101:2376           v1.10.3
```

可以看到 docker 已被更新到最新的版本。

有些時候 docker 會有些問題，不妨升級看看，說不定官方已經解決。
