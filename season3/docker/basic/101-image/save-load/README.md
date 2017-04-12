# 備份與載入映像檔


執行 `docker save` 指令將映像檔備份為 `ubuntu-latest.tar`：

```
docker save -o ubuntu-latest.tar ubuntu:latest
```

如此一來，我們就能將 `ubuntu-latest.tar` 透過 USB 隨身碟等方式複製到其他電腦。

取得 `ubuntu-latest.tar` 的電腦，即可用 `docker load` 指令載入映像檔。

```
docker load --i ubuntu-latest.tar
```

如果遇到需要在沒有網路的環境下離線作業，或是不想透過網路傳輸體積大的映像檔，`docker save` 與 `save load` 提供一個簡單實用的方式。
