java 開發環境安裝
=================

在一般標準開發環境下，我們需要安裝 Java 相關的 library，其安裝指令如下

```
apt-get install software-properties-common
add-apt-repository ppa:openjdk-r/ppa -y
apt-get update
apt-get install openjdk-8-jdk
apt-get install maven
```

若要自行建置 docker 的 java 運行環境透過 Dockerfile，我們需要先使用 base image 為 `ubuntu:latest`

使用 Dockerfile 時，一旦開始進行建置，Docker 會把 Dockerfile 所在位置底下所有的檔案載入以便建置過程中使用，為了加速建置程序，一般來說一個 Dockerfile 請放置於獨立的資料夾

### 建立 Dockerfile 存放之資料夾

```
mkdir java8-maven3-build
cd java8-maven3-build
```

### 建立 Dockerfile

```
cat > Dockerfile <<EOL
FROM ubuntu:latest

RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:openjdk-r/ppa -y
RUN apt-get update
RUN apt-get install -y openjdk-8-jdk
RUN apt-get install -y maven
EOL
```

### 進行 Dockerfile build

```
docker build -t trunk/java8-maven3-build .
```

確認 Dockerfile build 完成
--------------------------

`docker images`

查看是否有剛剛 commit 完成的 images，預期將看到下面內容

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
trunk/java8-maven3-build      latest              b8ce33c94dcc        8 seconds ago       737.1 MB
```

表示已經完成開發環境的建置

確認 docker image 可以正確運行
------------------------------

透過下面指令確認 docker 之 java 及 maven 版本

`docker run --rm trunk/java8-maven3-build java -version`

```
openjdk version "1.8.0_72-internal"
OpenJDK Runtime Environment (build 1.8.0_72-internal-b15)
OpenJDK 64-Bit Server VM (build 25.72-b15, mixed mode)
```

`docker run --rm trunk/java8-maven3-build mvn -v`

```
Apache Maven 3.0.5
Maven home: /usr/share/maven
Java version: 1.8.0_72-internal, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-openjdk-amd64/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.1.19-boot2docker", arch: "amd64", family: "unix"
```

如此就完成 docker 之 java 環境建置。
