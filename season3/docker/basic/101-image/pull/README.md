# 取得映像檔

使用 `docker pull` 指令從 Docker Hub 下載映像檔。

例如取得最新的 Ubuntu Linux 作業系統映像檔，執行：

```
docker pull ubuntu
```

終端機將會出現下面訊息：

```
Using default tag: latest
latest: Pulling from library/ubuntu

d38575f188e0: Pull complete
b04ea90f261c: Pull complete
40dc9cd44ffa: Pull complete
a3ed95caeb02: Pull complete
Digest: sha256:4bc45eecd925cb8806294d0e8bc5c1cfd1149c6dd8a5ef2165b6c02eabb8821f
Status: Downloaded newer image for ubuntu:latest
```

實際上這條指令省略了兩個參數內容：

1. Registry（註冊伺服器）
2. Tag（版本標記）

加上 Tag 版本標記，明確指定取得 `ubuntu:14.04`（目前的最新版本）的映像檔。

```
docker pull ubuntu:14.04
```

以下指令的執行結果與 `docker pull ubuntu` 相同。

```
# 加上 Tag 指定最新版
docker pull ubuntu:latest

# 加上 Registry，指定以 Docker Hub 註冊伺服器作為來源
docker pull registry.hub.docker.com/ubuntu

# 同時指定 Registry 與 Tag
docker pull registry.hub.docker.com/ubuntu:latest

# 指定以 DockerPool 註冊伺服器作為來源
docker pull dl.dockerpool.com:5000/ubuntu
```

備註：除了 Docker Hub 或 DockerPool 也可以搭配自行架設的私有註冊伺服器（Registry Server）。

## 更新映像檔

如果使用 `latest` 版本標記取得映像檔，日後可以重新執行 `docker pull` 檢查更新。

例如當 `ubuntu` 發佈更新後執行：

```
docker pull ubuntu
```

或

```
docker pull ubuntu:latest
```

就可以更新為最新版本。
