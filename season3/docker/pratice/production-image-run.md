# 使用 production image 運行專案進行 preview

難易度：進階

## 練習說明

完成範例專案之 production image 建置後，我們需要能夠使用該 image 進行實際運作

需要完成以下需求：

1. 透過 docker run 運行建置好的 production image
2. 將 container 內的 port 8000 與 host port 8000 mapping 並且開放
3. 在運行時給予別名 preview
4. 確保下次使用 docker run 時，是新建一個 docker container

請將上述步驟相關指令完成並且正確執行。
