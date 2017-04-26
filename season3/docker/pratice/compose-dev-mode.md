# 製作 docker-compose 之 dev mode service

難易度：進階

## 練習說明

在之前的章節中，我們可以透過

```
docker run -it ubuntu:latest /bin/bash
```

來進入 docker container

透過 volume 來進行相關檔案掛載，如：

```
docker run -v `pwd`:/app -v /root/.m2 -w /app maven:3-jdk-8 mvn install
```

透過上述兩個指令的組合可以完成透過 docker 來進行 java 語言環境進行軟體開發。

針對範例專案，請完成透過 docker-compose.yml 關於 dev mode 的定義，也就是說可以進入 docker 中 java 語言環境進行軟體開發。

需要完成以下需求

1. 使用 `maven:3-jdk-8` image
2. 將範例專案相關檔案掛載到 container 之 `/app` 資料夾
3. 使用 `volumes-from` 或使用 `volume` 將 `~/.m2` maven cache 掛載到 container，container 內 mavne cache 路徑為 `/root/.m2`
4. workdir 為 `/app`
5. 將 container port 8000 與 host 8000 port 進行 mapping
6. 執行指令為 `/bin/bash`
7. 透過 `docker-compose run --service-ports dev` 來進行運作
8. 完成透過 docker 來進行 java 語言環境進行軟體開發

請將上述步驟轉換為 docker-compose 的相關處理。
