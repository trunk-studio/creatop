# 直接掛載 host 指定之 path


## 建立 test folder

`mkdir test && ls -al test`

輸出訊息為

```
total 8
drwxrwxr-x 2 user user 4096 Jun  1 09:21 .
drwxr-xr-x 9 user user 4096 Jun  1 09:21 ..
```

## 使用 -v 進行 volume

```
docker run --rm \
-v `pwd`/test:/root/test \
ubuntu \
touch /root/test/readme.md
```

執行

`ls -al test`

確認輸出產出檔案

```
total 8
drwxrwxr-x 2 user user 4096 Jun  1 09:24 .
drwxr-xr-x 9 user user 4096 Jun  1 09:21 ..
-rw-r--r-- 1 root root    0 Jun  1 09:24 readme.md
```

在 docker 內所產生或操作的檔案，將直接同步到 host 的資料夾
