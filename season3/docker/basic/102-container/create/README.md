# 建立容器

先確認本機已有 `ubuntu:latest` 映像檔。

```
docker pull ubuntu
```

執行 `docker create` 指令新建一個容器。

```
docker create -it ubuntu:latest
```

為什麼需要 `-it` 參數呢？實際上這是 `-i` 與 `-t` 兩個參數的縮寫。

* `-i`

  Keep STDIN open even if not attached

* `-t`

  Allocate a pseudo-TTY

使用 `docker ps` 檢視所有容器的狀態。

```
docker ps -a
```

```
CONTAINER ID      IMAGE             COMMAND
2c06ac467b38      ubuntu:latest     "/bin/bash"
```

因為 `docker create` 指令建立的容器預設為停止狀態，所以加上參數 `-a` 才能顯示包含已停止的容器。

從上面的執行結果，我們可以得知容器的 `CONTAINER ID`，利用 ID 來啟動（或停止）容器。

啟動容器：

```
docker start 2c0
```

通常我們對容器進行操作時，為了讓指令輸入方便，並不會使用完整的 `CONTAINER ID`，只要輸入前三碼字母即可。

容器啟動後，再以 `docker ps` 查詢執行中的容器，可以看到 STATUS 的變化。

```
docker ps
```

停止容器，使用 `docker stop` 指令。

```
docker stop 2c0
```
