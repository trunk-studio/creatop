透過 Docker Machine 建立 Docker Engine
======================================

VirtualBox
----------

建立 virtualBox 的 Docker Engine 是最簡單的，執行下列指令即可

`docker-machine create -d virtualbox dev`

如此就會在你的 virtualBox 建立一 dev 的虛擬機

DigitalOcean
------------

建立 DigitalOcean 之 docker Machine 首先必須要有 Access Token，我們可以把屬於你的 Token 透過環境變數載入，Docker 將會預設讀取對應的變數名稱，範例如下

`export DIGITALOCEAN_ACCESS_TOKEN=123456`

接著就可以指定 Driver 以及你所希望對應的 image

```
docker-machine create \
--driver digitalocean \
--digitalocean-image ubuntu-15-10-x64 \
digitalocean-dev
```
