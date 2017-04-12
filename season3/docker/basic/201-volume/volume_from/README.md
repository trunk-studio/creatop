# 從 docker 進行 volume

與直接 create 不同，將檔案實體存在 docker 內，所以無法在 host 直接存取檔案

## run docker 並給予別名

```
docker run \
--name sample-data \
-v /root/test \
ubuntu
```

## 使用 volumes-from 並建立一個檔案

```
docker run --rm \
--volumes-from sample-data \
ubuntu \
touch /root/test/readme.md
```

## 再次確認該檔案確實存在

```
docker run --rm \
--volumes-from sample-data \
ubuntu \
ls -al /root/test
```

輸出訊息如下

```
total 8
drwxr-xr-x 2 root root 4096 Jun  1 09:13 .
drwx------ 3 root root 4096 Jun  1 09:18 ..
-rw-r--r-- 1 root root    0 Jun  1 09:13 readme.md
```
