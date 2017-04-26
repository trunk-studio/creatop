# java 範例專案運行測試

## 範例 github repository

<https://github.com/agileworks-tw/spring-boot-sample>

## clone repository

透過下面指令，將會複製範例專案

`git clone git@github.com:agileworks-tw/spring-boot-sample.git`

## pull java 8 and maven 3 docker image

`docker pull maven:3-jdk-8`

## 透過 docker image 進行專案套件安裝

運行指令如下：

```
docker run \
--name sample-java-install \
-v `pwd`:/app \
-v /root/.m2 \
-w /app \
maven:3-jdk-8 \
mvn install
```

## `-v` or `--volume`

使用了兩次：

1. `${pwd}:/app`: 將目前專案所在目錄掛載到 docker container 中的`/app` 路徑
2. `$HOME/.m2:/root/.m2`: 將 docker 內的 maven cache 掛載到 host 以加快後續的建置

另外一個方式就是使用 docker volume container

```
docker run \
--name sample-java-data \
-v /root/.m2 \
ubuntu
```

如此我們就可以讓每次建置都使用同一個 docker volume container，注意這邊

```
docker run --rm \
-v `pwd`:/app \
--volumes-from sample-java-data \
-w /app \
maven:3-jdk-8 \
mvn install
```

上述指令執行第二次時，maven 就不會再次 download 相關 jar 檔，`sample-java-data` container 也可以作為後續建置所需的 cache 來源。

## `-w` or `--workdir`

為執行 CMD 所在檔案路徑，也就是說 `mvn install` 將會在 container 中的 `/app` 執行，而因為 `-v` 已將範例專案掛載到 `/app` 就像在 host 執行指令一樣。

## 執行安裝指令

最後使用 `maven:3-jdk-8` image 則為官方提供的 maven 環境。

`mvn install` 則為此次建置要使用的 command 將此專案所需的套件進行安裝。

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
mvn install
```

轉換為 docker-compose.yml 其檔案內容如下：

```
data:
  image: ubuntu
  volumes:
    - /root/.m2

install:
  image: maven:3-jdk-8
  volumes:
    - ./:/app
  volumes_from:
    - data
  working_dir: /app
  command: "mvn install"
```

### 透過 docker-compose 運行專案安裝

`docker-compose run install`

`volumes_from` 允許格式如下

```
volumes_from:
 - service_name
 - service_name:ro
 - container:container_name
 - container:container_name:rw
```

因為 `volumes_from` 的定義當我們運行 `install` 的 service 時，docker-compose 會連帶的將 `data` service 一併帶起
