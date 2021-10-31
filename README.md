# Dockerを使ったCentOS6とMySQL

## 概要

Dockerを使ってCentOS6とMySQLの環境を構築するための環境。

## 使い方

### CentOS6の起動への対応

### Windows

wslで起動する場合は"C:\Users\<yourUserName>\.wslconfig"に設定を追加する。  
yourUserNameは自分のユーザネームに置き換える。
```.wslconfig
kernelCommandLine = vsyscall=emulate
```

### LLinux

ブートローダのカーネルオプションに設定を追加する。
```
vsyscall=emulated
```

### 起動方法

centos6/htmlフォルダにコンテンツを入れる。  
centos6/dockerfileを必要に応じて更新する。  

webサーバの設定
phpのバージョンはdockerfileの環境変数phpverに定義する。  
mysqlクライアントのバージョンはdockerfileの環境変数mysqlverに定義する。  
``` dockerfile
# 中略
ENV phpver 56
# 中略
ENV mysqlver 56
```

dbサーバのバージョン指定はdocker-composeで指定する。
```yaml
services:
  db:
    container_name: db
    image: mysql:5.7
# 以下略
```

dockerファイル定義したイメージは  
docker-composeコマンドを使ってコンテナビルドして起動する。  
初回起動時はイメージをビルドして起動する。  
``` bash
docker-compose up --build -d
```

コンテナの更新がなければstartコマンドで起動する。  
``` bash
docker-compose start
```

### 停止方法

docker-compose.ymlがあるディレクトリで下記のコマンドを実行する。  

```
docker-compose stop
```


## 参考

- [docker-compose "up" " run" "start" コマンド 違い](https://qiita.com/mom0tomo/items/f536e6759d3f42d58ffc)
- [centos docker official image ](https://hub.docker.com/_/centos)