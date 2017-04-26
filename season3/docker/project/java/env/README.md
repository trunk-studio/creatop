java 開發環境安裝
=================

在一般標準開發環境下，我們需要安裝 Java 相關的 library

安裝 java 8 & maven
-------------------

```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
sudo apt-get install maven
```

選擇 java 8 作為預設 java version
---------------------------------

```
sudo update-alternatives --config java
sudo update-alternatives --config javac
```

確認 java 及 maven 安裝完成
---------------------------

```
java -version
maven -v
```
