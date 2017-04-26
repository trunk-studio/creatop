# java 範例專案打包

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
mvn package
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
mvn package
```

相關說明可以參考 [java project install](../install/README.md)

## 執行打包指令

最後使用 `maven:3-jdk-8` image 則為官方提供的 maven 環境。

`mvn package` 將會專案打包程序，執行完成後，將會看到下列訊息

`Building jar: /app/target/spring-boot-sample-data-rest-0.1.0.jar`

代表建置完成。

## 透過 docker compose 運行

### 將 docker command 轉換為 docker-compose

以下面的指令為例

```
docker run \
--name sample-java-data \
-v /root/.m2 \
ubuntu
```

```
docker run --rm \
-v `pwd`:/app \
--volumes-from sample-java-data \
-w /app \
maven:3-jdk-8 \
mvn package
```

轉換為 docker-compose.yml 其檔案內容如下：

```
data:
  image: ubuntu
  volumes:
    - /root/.m2

package:
  image: maven:3-jdk-8
  volumes:
    - ./:/app
  volumes_from:
    - data
  working_dir: /app
  command: "mvn package"
```

### 透過 docker-compose 運行專案安裝

`docker-compose run package`
