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

若要自行建置 docker 的 java 運行環境，我們需要先取得 base image，我們使用 `ubuntu:latest`

pull ubuntu 作為 base image
---------------------------

`docker pull ubuntu:latest`

一但執行完成後，我們可透過 run 進入 ubuntu container

run ubuntu with TTY
-------------------

`docker run -it ubuntu:latest /bin/bash`

將會看到類似，ID 會因為每個人而有所不同，此 ID 將會在安裝完成後進行後續操作識別用

`root@94fe61e92bbb:/#`

表示目是已經可以對 ubuntu docker container 進行操作，接著我們可以執行 java 相關運行環境的安裝

```
apt-get install software-properties-common
add-apt-repository ppa:openjdk-r/ppa -y
apt-get update
apt-get install openjdk-8-jdk
apt-get install maven
```

安裝完成後，透過下列指令確認安裝正確

`java -version`

正確將輸出下面內容

```
openjdk version "1.8.0_72-internal"
OpenJDK Runtime Environment (build 1.8.0_72-internal-b15)
OpenJDK 64-Bit Server VM (build 25.72-b15, mixed mode)
```

`mvn -v`

正確將輸出下面內容

```
Apache Maven 3.0.5
Maven home: /usr/share/maven
Java version: 1.8.0_72-internal, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-openjdk-amd64/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.1.19-boot2docker", arch: "amd64", family: "unix"
```

將 Container commit 為 java8-maven3 image
-----------------------------------------

首先退出 ubuntu Container

```
root@94fe61e92bbb:/# exit
```

一旦退出後 container `94fe61e92bbb` 將會立即停止，透過

`docker ps -a`

查看目前所有 Container 的狀態，如下

```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                       PORTS               NAMES
94fe61e92bbb        ubuntu:latest       "/bin/bash"              20 minutes ago      Exited (130) 8 seconds ago                       admiring_elion
```

接著我們可以把 container `94fe61e92bbb` commit 為新的 image

`docker commit 94fe61e92bbb trunk/java8-maven3`

透過

`docker images`

查看是否有剛剛 commit 完成的 images，預期將看到下面內容

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
trunk/java8-maven3            latest              2c9577331819        8 seconds ago       732.4 MB
```

表示已經完成開發環境的建置

確認 docker image 可以正確運行
------------------------------

透過下面指令確認 docker 之 java 及 maven 版本

`docker run --rm trunk/java8-maven3 java -version`

```
openjdk version "1.8.0_72-internal"
OpenJDK Runtime Environment (build 1.8.0_72-internal-b15)
OpenJDK 64-Bit Server VM (build 25.72-b15, mixed mode)
```

`docker run --rm trunk/java8-maven3 mvn -v`

```
Apache Maven 3.0.5
Maven home: /usr/share/maven
Java version: 1.8.0_72-internal, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-8-openjdk-amd64/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "4.1.19-boot2docker", arch: "amd64", family: "unix"
```

如此就完成 docker 之 java 環境建置。
