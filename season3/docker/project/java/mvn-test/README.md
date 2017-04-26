# java 範例專案運行測試

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
maven:3-jdk-8 \
mvn test
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
maven:3-jdk-8 \
mvn test
```

相關說明可以參考 [java project install](../install/README.md)

## 執行測試指令

最後使用 `maven:3-jdk-8` image 則為官方提供的 maven 環境。

`mvn test` 將會運行預先寫好的 test case，完成專案測試運行。
