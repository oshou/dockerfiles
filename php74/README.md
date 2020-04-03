# php7.4

## 概要

- php7.4環境を起動いたします。
- **port9001で起動いたします。**
- 変更する場合は、php-fpm/conf/www.confのlisten欄を設定して下さい。
- 必要によりwebコンテナとのつなぎこみをお願いいたします。
  /etc/nginx/conf.d/default.confへの127.0.0.1:9001への定義追加等

## 起動手順
```
- dockerインストール
  (コンテナ管理に使います)
  https://qiita.com/ymasaoka/items/b6c3ffea060bcd237478

- インストール後バージョン確認
  docker version

- docker-compose install
  (主にローカルで複数コンテナを組み合わせり設定をカスタムしたい場合に使います。)
  https://docs.docker.com/compose/install/

- インストール後バージョン確認
  docker-compose version
```

## 起動手順

```
# Dockerデーモン起動
$ systemctl start docker

# Docker関連ファイルインストール
$ git clone https://github.com/oshou/dockerfiles

# アプリケーションのディレクトリ指定
$ export SRC_DIR=/path/to/your_application_directory

# コンテナ起動
$ export SRC_DIR=/path/to/your_application_directory
$ cd dockerfiles/php74
$ docker-compose up -d
```
