# link container

container 在使用使很多時候需要跟多個 container 進行溝通，舉例來說，在 docker 的使用上，很多時候我們會將前端跟後端如 DB 分為兩個 container。

## 啟動 DB container

`docker run -d --name db training/postgres`

## 啟動 web container 並且透過 link 與 DB 進行溝通

`docker run --name web --link db:db training/webapp ping db`

一旦有 link 的 option 定義，就可以直接透過 container name 進行存取，上述指令執行後將出現

```
PING db (172.17.0.2) 56(84) bytes of data.
64 bytes from db (172.17.0.2): icmp_seq=1 ttl=64 time=0.065 ms
64 bytes from db (172.17.0.2): icmp_seq=2 ttl=64 time=0.056 ms
64 bytes from db (172.17.0.2): icmp_seq=3 ttl=64 time=0.060 ms
```

代表 ip 是正常可以存取的

透過下面指令，我們可以查詢到哪些 container 是 link 在一起的


`docker inspect -f "{{ .HostConfig.Links }}" web`

將輸出

`[/db:/web/db]`


我們可以再進一步驗證，拿掉 `--link db:db`

```
docker rm -f web
docker run --name web training/webapp ping db
```

此時輸出的訊息為

`ping: unknown host db`
