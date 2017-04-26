Docker Machine env
==================

為了能夠操作多台 Docker Engine，Machine 會把相關的資訊存在你的 `$HOME/.docker/machine` 底下，若需要讀取時，你可以透過

`docker-machine env`

來進行存取。

首先，透過 create 一 docker Engine 透過 driver 為 virtualBox

`docker-machine create -d virtualbox test`

`docker-machine create -d virtualbox dev`

建立好之後，我們可以透過 `env` 指令來查看相關的資訊

`docker-machine env test`

將可以看到類似下面的訊息

```
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.101:2376"
export DOCKER_CERT_PATH="/Users/spooky/.docker/machine/machines/test"
export DOCKER_MACHINE_NAME="test"
# Run this command to configure your shell:
# eval $(docker-machine env test)
```

若是查看 `dev`

`docker-machine env dev`

將可以看到

```
export DOCKER_TLS_VERIFY="1"
export DOCKER_HOST="tcp://192.168.99.100:2376"
export DOCKER_CERT_PATH="/Users/spooky/.docker/machine/machines/dev"
export DOCKER_MACHINE_NAME="dev"
# Run this command to configure your shell:
# eval $(docker-machine env dev)
```

不同的 Docker Engine 其對應的資訊將會有所不同

可以看到最後的註解

```
# Run this command to configure your shell:
# eval $(docker-machine env test)
```

我們可以透過下面指令切換到 test

`eval $(docker-machine env test)`

也可以透過下面指令切換到 dev

`eval $(docker-machine env dev)`

透過指令的執行把相關 environment 載入，當你需要管理多台 Docker Engine 時，不只是本地的 VM 遠端的 cloud 也可以透過類似的方式進行 Docker 的管理跟操作，將會是很方便的 tool。
