# network create

透過 network create 並且在運行 container 時，透過指定 network 也可以讓 container 進行溝通

## 建立 default bridge

`docker network create -d bridge test_net`

## 運行 docker 加入 network option



### 啟動 DB container

`docker run -d --net test_net --name db training/postgres`


`docker network inspect test_net`

```
"Containers": {
    "0a7013db1d5cf56797312eed7fe7894a62d57f7476c4777f5ab4922e38c8aa2a": {
        "Name": "db",
        "EndpointID": "32e4cd2a6ad0feb1af567e1ca6fbc3f5300c7c6c1745ec1754cab6a17858b0f9",
        "MacAddress": "02:42:ac:15:00:02",
        "IPv4Address": "172.21.0.2/16",
        "IPv6Address": ""
    }
},
```

若如下沒有加 net option 預設為 default 如下

`docker run --name web training/webapp ping 172.21.0.2`

將沒辦法 ping 到，若同樣加上 --net test_net

`docker run --name web --net test_net training/webapp ping 172.21.0.2`

將顯示

```
PING 172.21.0.2 (172.21.0.2) 56(84) bytes of data.
64 bytes from 172.21.0.2: icmp_seq=1 ttl=64 time=0.064 ms
64 bytes from 172.21.0.2: icmp_seq=2 ttl=64 time=0.109 ms
64 bytes from 172.21.0.2: icmp_seq=3 ttl=64 time=0.131 ms
64 bytes from 172.21.0.2: icmp_seq=4 ttl=64 time=0.070 ms
```

表示連線正常
