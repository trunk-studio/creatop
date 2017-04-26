使用 docker-machine 連結已存在之遠端 docker engine
==================================================

假設你已經有個 remote 的 ubuntu server，在該 server 上已經有安裝 docker engine，一般來說你需要管理 docker 時，可能就需要透過 ssh 連上 server 之後進行 docker 的操作。

透過 docker-machine 之 generic driver 將可以已讓你在你的電腦集中管理已存在的 ubuntu server。

ubuntu user 必須是 sudo 並且使用 sudo 時不需要 password
-------------------------------------------------------

若你不是用 root 帳號，可以透過下列指令，讓你的 linux user 符合條件

```
sudo visudo
```

```
yourname ALL=(ALL) NOPASSWD: ALL
```

輸入 Ctrl-X 離開，你的 user 進行 sudo 時將不再需要打密碼，如此才可進行 docker-machine 建立

建立 docker-machine
-------------------

```
docker-machine create \
--driver generic \
--generic-ip-address=11.22.33.44 \
--generic-ssh-key=~/.ssh/id_rsa \
ubuntuvm
```

載入環境變數進行 Docker engine 操作
-----------------------------------

```
eval "$(docker-machine env ubuntuvm)"
```

如此一來你就可以在你的電腦操做已存在之 remote docker engine
