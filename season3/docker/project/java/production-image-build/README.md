# 建立 production mode image

## 建立 Dockerfile

```
FROM java:8-jdk
COPY target/spring-boot-sample-data-rest-0.1.0.jar /app/
EXPOSE 8000
WORKDIR /app
CMD /bin/bash -c 'java -jar spring-boot-sample-data-rest-0.1.0.jar'
```

因為是 production mode 我們只需要最後打包完成的檔案，所以儘可能精簡執行所需的套件

## 執行建置指令

需要注意的是，一旦運行 `docker build`，docker 檔案的存取只能局限於 docker build 運行的所在位置。

因為 build 的指令是直接使用 `spring-boot-sample-data-rest-0.1.0.jar` 所以在 build 之前我們可以先運行 package 指令

```
docker run --rm \
-v `pwd`:/app \
-v $HOME/.m2:/root/.m2 \
-w /app \
maven:3-jdk-8 \
mvn package
```

如此就會產生對應的 jar 檔，接著我們就可以進行 production image 的建置

```
docker build -t agileworks/spring_prod .
```

## 運行 production image

```
docker run -p 8000:8000 agileworks/spring_prod
```
