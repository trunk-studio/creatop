# 進入容器

正在背景狀態執行的容器，可以利用 `docker exec` 執行新的 Bash Shell。

```
docker exec -ti 374 /bin/bash
```

或是執行指令，例如 `ps aux`：

```
docker exec -ti 374 ps aux
```

輸出結果：

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND        
root         1  0.0  0.2  12832  2048 ?        Ss+  11:01   0:00 ping google.com
root        26  0.0  0.2  15572  2176 ?        Rs+  11:01   0:00 ps aux
```

也可以利用 `docker attach` 指令，切換至容器的終端機。

```
docker attach 374
```

如果有多位使用者操作同一個容器，通常執行 `exec` 會比 `attach` 合適，因為 `attach` 會讓每個使用者共用同一個終端機畫面，因此造成互相牽制影響。
