# 移除容器

列出所有容器（包含停止狀態的容器）。

```
docker ps -a
```

輸出如下：

```
CONTAINER ID        IMAGE               COMMAND
270ea7ee8b06        ubuntu              "/bin/bash"
```

如果要移除 `270ea7ee8b06` 這個容器，可以執行 `docker rm ` 指令：

```
docker rm 270
```

假如容器還在運行中會出現錯誤，加上 `-f` 參數可以強制移除容器。

```
docker rm -f 270ea7ee8b06
```

如果同時要移除（或停止）所有容器，可以搭配以下 Shell 指令進行：

先停止所有容器。

```
docker stop $(docker ps -a -q)
```

再移除所有容器。

```
docker rm $(docker ps -a -q)
```
