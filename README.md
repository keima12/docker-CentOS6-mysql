# Dockerを使ったCentOS6とMySQL

## 概要

Dockerを使ってCentOS6とMySQLの環境を構築するための環境。

## 使い方

### 起動方法
centos6/htmlフォルダにコンテンツを入れる。  
centos6/dockerfileを必要に応じて更新する。  
docker-composeコマンドでコンテナを起動する。  

```
docker-compose up -d
```

### 停止方法

docker-compose.ymlがあるディレクトリで下記のコマンドを実行する。  

```
docker-compose stop
```
