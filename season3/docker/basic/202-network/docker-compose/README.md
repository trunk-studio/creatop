# 透過 docker-compose 使用 network

範例專案： <https://github.com/agileworks-tw/docker-basic-sample.git>

## docker-compose

```
version: '2'
services:
  web:
    image: hiromasaono/curl
    networks:
      - back-tier

  nginx:
    image: nginx
    networks:
      - back-tier

networks:
  back-tier:
    driver: bridge
  front-tier:
    driver: bridge
```

上面的 docker-compose 我們可以先透過下列指令

```
docker-compose up nginx
```

接著

```
docker-compose run web /bin/bash
```

進入 docker container 內之後執行

```
ping nginx
```

將會顯示

```
64 bytes from network_nginx_1.network_back-tier (172.21.0.2): icmp_seq=1 ttl=64 time=0.108 ms
64 bytes from network_nginx_1.network_back-tier (172.21.0.2): icmp_seq=2 ttl=64 time=0.134 ms
64 bytes from network_nginx_1.network_back-tier (172.21.0.2): icmp_seq=3 ttl=64 time=0.099 ms
```

則表示網路是可以通的，若我們把上面的 docker-compose 內容改為

```
version: '2'
services:
  web:
    image: hiromasaono/curl
    networks:
      - front-tier

  nginx:
    image: nginx
    networks:
      - back-tier

networks:
  back-tier:
    driver: bridge
  front-tier:
    driver: bridge
```

此時進行上面的指令，將會出現

```
ping: unknown host nginx
```

使用 docker network 可以很方便地進行環境建置，即使是不同的 container 也可以很方便的組合
