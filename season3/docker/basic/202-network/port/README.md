# port

port 與 expose 有所不同，port 設置主要是要讓 container 與 host 進行溝通

下述的設置，將可以讓 container 內的 80 port 可以從 host 8888 port 進行存取

`docker run --name nginx -d -p 8888:80 nginx`

一旦運行完成後可以執行下述指令驗證

`curl http://localhost:8888`

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

表示已正確存取 nginx 的 welcome page

若不指令 host port 的話

`docker run --name nginx -d -p 80 nginx`

docker 將會自行指定 random port 以便 host 可以存取，透過 docker ps 來看一下

```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                            NAMES
f614261df0b1        nginx               "nginx -g 'daemon off"   2 seconds ago       Up 1 seconds        443/tcp, 0.0.0.0:32776->80/tcp   nginx
```

將可以透過 `http://localhost:32776` 存取 nginx
