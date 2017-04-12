# 背景執行

讓一個長時間執行的指令在背景運作，可以利用 `-d` 參數。

```
docker run -d -it ubuntu ping google.com
```

參數說明：

* `-d` 表示讓程式在後台以背景狀態（Daemonized）的形式執行。

透過 `docker ps` 查詢容器的狀態：

```
CONTAINER ID        IMAGE               COMMAND
374fb78dab41        ubuntu              "ping google.com"
```

要如何檢視 `ping google.com` 指令的輸出呢？可以透過 `docker logs` 指令：

```
docker logs 374
```

如果想要持續顯示最新的輸出，也可以加上 `-f` 參數（結束用 Ctrl + C 組合鍵）：

```
docker logs -f 374
```
