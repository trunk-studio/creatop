# 範例專案以 Java 為例

為了可以將 Docker 或 Jenkins 實際應用在日常開發或是部署上，需要先了解一個專案的基本結構，此章節將說明在開發中一個標準的專案須有哪些環節需要注意，此章節開始前，假設已經完成 Java 8 以及 Maven 3 的安裝。

## 範例 github repository

<https://github.com/agileworks-tw/spring-boot-sample>

## clone repository

透過下面指令，將會複製飯粒專案

`git clone git@github.com:agileworks-tw/spring-boot-sample.git`

## 建置專案

透過下列指令將會把 maven pom.xml 中定義的套件進行安裝

`mvn install`

## 測試專案

透過下列指令，將會運行自動測試。

`mvn test`

## 運行專案

透過下列指令，將會運行 development mode 作為開發中方確認結果。

`mvn spring-boot:run`

透過下列網址

`http://localhost:8000/api`

可以存取範例專案運行結果

## 打包專案

`mvn package`

執行完，將會看到訊息

```
[INFO] Building jar:
/Users/spooky/projects/agileWorks/spring-boot-sample/target/spring-boot-sample-data-rest-0.1.0.jar
```

## production run

```
java -jar \
/Users/spooky/projects/agileWorks/spring-boot-sample/target/spring-boot-sample-data-rest-0.1.0.jar
```

透過下列網址

`http://localhost:8000/api`

可以存取 production mode 範例專案運行結果。
