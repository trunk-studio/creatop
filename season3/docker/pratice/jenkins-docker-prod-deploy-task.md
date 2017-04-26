# jenkins 建立 production deploy task

難易度：進階

## 練習說明

使用 jenkins 建立範例專案之 production deploy task

需要完成以下需求：

### task shell script

目的：完成 production image 建立，並且發佈到 docker hub

1. 透過 docker login 進行登入
2. 透過 docker-compose 進行專案建置
3. 透過 docker build 進行 production image 建置
4. 透過 docker push 將建立好的 docker 發佈到 docker hub

### 透過 ssh 連線到 production 機器運行建置好的 image

1. 使用 ssh 連到 localhost（模擬連線到遠端機器）
2. 透過 docker pull 取得更新完成的 production image
3. 將 container 內的 port 8800 與 host port 8800 mapping 並且開放
4. 在運行時給予別名 prod
5. 確保下次使用 docker run 時，是新建一個 docker container 重新運作
6. 加上 restart always 令主機重開時能夠自動重啟 docker container

請將上述步驟相關指令完成並且正確執行。
