列出所有 docker-machine 相關資訊
================================

跟 docker image 或是 container 一樣，若要查詢相關資訊，也可以透過 docker-machine 所提供的 `ls` 來檢視目前管理的 docker engine 有哪些。

假設我們透過 docker-machine 建立兩個 virtualBox 之 Docker engine

`docker-machine create -d virtualbox test`

`docker-machine create -d virtualbox dev`

並且透過 `env` 載入環境變數進行 docker 操作，透過下列指令

`eval $(docker-machine env dev)`

接著執行

`docker-machine ls`

將會看到下面輸出

```
NAME       ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
dev        *        virtualbox   Running   tcp://192.168.99.100:2376           v1.10.2
test       -        virtualbox   Running   tcp://192.168.99.101:2376           v1.10.3
```

其中可以看到

-	ACTIVE: 打上 `*` 表示正在操作的 Docker engine
-	STATE: Docker engine 狀態
-	URL: engine 所在 ip
-	SWARM: 是否為 SWARM master or node，後續章節會再行介紹
-	DOCKER: 建立 Docker 時所安裝的 Docker 版本
