# volume

volume 屬於 docker 很重要的一環，除了運行相關程式之外，檔案操作與存放是專案在運行時不可或缺的

docker volume 提供下列指令


```
Usage:	docker volume [OPTIONS] [COMMAND]

Manage Docker volumes

Commands:
  create                   Create a volume
  inspect                  Return low-level information on a volume
  ls                       List volumes
  rm                       Remove a volume
```

以往需要透過 docker 的運行來進行 volume 來進行，現在我們可以透過 docker volume 直接定義
