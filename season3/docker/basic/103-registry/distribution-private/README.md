# private registry server

若有需要自行架設 private registry server 可以參考下列網址

[docker/distribution](https://github.com/docker/distribution/blob/master/docs/deploying.md)

- 舊版 private registry server 1.0 之 github repository 網址為 <https://github.com/docker/docker-registry>
- 新版 private registry server 2.0 之 github repository 網址為 <https://github.com/docker/distribution>

會有新舊之分，主要是舊版是用 python 實作，新版則改用 go 來實作，以便改善安全性及效能。

對 docker 而言架設一個 registry server 就是啟動一個 container，相關操作練習步驟如下。

## 啟動 private registry server

`docker run -d -p 5000:5000 --restart=always --name registry registry:2`

## 從 docker hub/public registry server 取得 ubuntu image

`docker pull ubuntu`

## 變更 ubuntu tag 為 private registry image

`docker tag ubuntu localhost:5000/ubuntu`

## 將 image push 到 private registry server

`docker push localhost:5000/ubuntu`

## 再次從 private registry server pull image

`docker pull localhost:5000/ubuntu`
