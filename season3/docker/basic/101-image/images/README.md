# 列出映像檔

執行 `docker images` 指令列出本機上已有的映像檔：

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
ubuntu                        latest              a1e4ed2ac65b        8 hours ago         188 MB
ubuntu                        14.04               07c86167cdc4        4 weeks ago         188 MB
```

* REPOSITORY

  代表映像檔所在的倉庫（Repository）名稱。

* TAG

  版本標記（若是在 `git pull` 時沒有指定版本，就會顯示 `latest` 代表預設的最新版本）。

* IMAGE ID

  映像檔的唯一識別編號（檔案的 SHA-1 Hash 編碼）。
