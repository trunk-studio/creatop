# 搜尋映像檔

使用 `docker search` 指令搜尋 Ubuntu Linux 相關的映像檔。

```
docker search ubuntu
```

搜尋結果的資料筆數非常多，如何篩選出我們需要的映像檔？

通常我們會從 STARS 數量評比來判斷映像檔的熱門程度，人氣指數愈高通常代表：由官方發行或功能完善且有持續更新維護。用 `-s 20` 篩選 STARS 數量大於 20 的映像檔：

```
docker search -s 20 ubuntu
```

執行結果：

```
NAME                       DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED      
ubuntu                     Ubuntu is a Debian-based Linux operating s...   3675      [OK]                      
ubuntu-upstart             Upstart is an event-based replacement for ...   61        [OK]                      
torusware/speedus-ubuntu   Always updated official Ubuntu docker imag...   25                   [OK]           
ubuntu-debootstrap         debootstrap --variant=minbase --components...   24        [OK]                      
rastasheep/ubuntu-sshd     Dockerized SSH service, built on top of of...   24                   [OK]
```

若要讓 search 敘述完整呈現可加上面下面的 Option：

```
--no-trunc         Don't truncate output
```
