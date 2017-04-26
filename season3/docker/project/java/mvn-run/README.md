# java 範例專案運行運行

## 範例 github repository

<https://github.com/agileworks-tw/spring-boot-sample>

## clone repository

透過下面指令，將會複製範例專案

`git clone git@github.com:agileworks-tw/spring-boot-sample.git`

## pull java 8 and maven 3 docker image

`docker pull maven:3-jdk-8`

## 透過 docker image 進行專案測試

運行指令如下：

```
docker run --rm \
-v `pwd`:/app \
-v $HOME/.m2:/root/.m2 \
-w /app \
-p 8000:8000 \
maven:3-jdk-8 \
mvn spring-boot:run
```

## `-v` or `--volume`

使用了兩次：

1. `${pwd}:/app`: 將目前專案所在目錄掛載到 docker container 中的`/app` 路徑
2. `$HOME/.m2:/root/.m2`: 將 docker 內的 maven cache 掛載到 host 以加快後續的建置

另外一個方式就是使用 docker volume container

```
docker run --rm \
-v `pwd`:/app \
--volumes-from sample-java-data \
-w /app \
-p 8000:8000 \
maven:3-jdk-8 \
mvn spring-boot:run
```

相關說明可以參考 [java project install](../install/README.md)

## `-p` or `--publish`

對於 docker container 而言，預設 container 是不對外開放 port 的，我們可以根據我們運行上的需要開放必要的 port。

`-p 8000:8000` 代表的意思就是將 container 內的 8000 publish 到 host 8000 port 令我們可以存取 service。

## 執行專案運行

最後使用 `maven:3-jdk-8` image 則為官方提供的 maven 環境。

`mvn spring-boot:run` 將會將專案運行，透過下列網址進行存取

<http://localhost:8000/api>
