其他有用指令
------

### extends

可以繼承於某一個特定的 docker-compose-yml

ex:

```
extends:
  file: common.yml
  service: webapp
```

### Variable substitution

與 extends 類似，不過可以透過 env 變數進行相關參數替換

ex:

```
db:
  image: "postgres:${POSTGRES_VERSION}"
```
