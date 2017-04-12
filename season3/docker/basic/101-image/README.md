Lab 101: Docker Image
======================

課程長度：15分鐘

難易度：基礎

----

映像檔（Image）是 Docker 的重要基礎概念，也是執行容器（Container）所必備。

* 映像檔類似 Ubuntu Live CD / USB 的 ISO。

映像檔與容器之間的關係？

* 如果把映像檔視為物件導向的類別（class），容器則可視為物件（object）。
* 啟動容器需要本機已存在所需映像檔。

映像檔從哪裡來？

* 來自 Docker 的倉庫（Repository）。
* 如果本機不存在所需映像檔，Docker 會嘗試從預設的倉庫（例如：Docker Hub）下載映像檔。

----

本單元將練習以下的 Docker 指令：

1. 搜尋映像檔

   `search`

2. 取得映像檔

   `pull`

3. 列出所有映像檔

   `images`

4. 檢視映像檔資訊

   `inspect`

5. 備份與載入

   `save`, `load`

6. 刪除映像檔

   `rmi`
