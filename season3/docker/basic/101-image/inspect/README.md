# 檢視映像檔資訊

先執行 `docker images` 查看映像檔：

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
ubuntu                        latest              a1e4ed2ac65b        8 hours ago         188 MB
ubuntu                        14.04               07c86167cdc4        4 weeks ago         188 MB
```

依據上面的清單內容，如果我們想檢視 `ubuntu:14.04` 的詳細資訊，可以執行 `docker inspect`：

```
docker inspect ubuntu:14.04
```

或是指定 IMAGE ID：

```
docker inspect a1e4ed2ac65b
```

執行 `inspect` 的輸出結果為 JSON 格式，在 Console 中可以搭配 `less` 方便捲動檢視。
