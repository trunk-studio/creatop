# 刪除映像檔

先執行 `docker images` 查看映像檔：

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
ubuntu                        latest              a1e4ed2ac65b        8 hours ago         188 MB
ubuntu                        14.04               07c86167cdc4        4 weeks ago         188 MB
```

依據上面的清單內容，如果我們想刪除 `ubuntu:14.04` 的映像檔，可以執行 `docker rmi`：

```
docker rmi ubuntu:14.04
```

刪除的動作有一個前提，該映像檔必須沒有運行的容器（Container），否則就會產生錯誤訊息。然而，如果確定要放棄 Container（可能導致容器資料流失），可加上 `-f` 參數強制刪除映像檔。

```
docker rmi -f ubuntu:14.04
```

實務上我們應避免直接強制刪除映像檔，正確的做法是，先刪除映像檔相關的所有容器，然後才刪除映像檔。
