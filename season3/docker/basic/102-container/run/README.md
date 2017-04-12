# 執行容器

使用 `docker run` 可以啟動一個容器，並執行自訂的 Command Line 指令。

```
docker run ubuntu /bin/echo Hello, Docker!
```

執行結果會輸出：

```
Hello, Docker!
```

實際上 `echo` 指令是在 Ubuntu Linux 作業系統容器中執行。

多試試其他 Ubuntu Linux 的指令，例如 `uname`：

```
docker run ubuntu /bin/uname -a                                 
```

輸出結果：

```
Linux 5d45430a0a54 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:26 UTC
2016 x86_64 x86_64 x86_64 GNU/Linux  
```

Docker Container 提供一個完全隔離的環境給 Ubuntu Linux，有別於傳統的虛擬機器，Docker 的容器十分輕量、隨時可以新建或刪除。


## 執行 Bash Shell

執行：

```
docker run -it ubuntu:14.04 /bin/bash
```

在 Container 的 Shell 試試一些常用的 Linux 指令：

* `ls`
* `ps`
* `pwd`
* `dmesg`
* `uname`

要結束 Shell 只要執行：

```
exit
```

退出後可以用 `docker ps -a` 觀察容器的狀態，可以發現每一次 Docker 執行完指令後，都會回到停止狀態。
