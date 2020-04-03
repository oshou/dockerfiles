# docker-lemp-stack

## 起動内容
合計3コンテナ起動いたします。
- [alpine] nginx v1.15
- [alpine] php-fpm(php7.4)
- [debian] MySQL v5.7

## 起動手順
```
- dockerインストール
  (コンテナ管理に使います)
  https://qiita.com/ymasaoka/items/b6c3ffea060bcd237478

- docker-compose install
  (主にローカルで複数コンテナを組み合わせり設定をカスタムしたい場合に使います。)
  https://docs.docker.com/compose/install/

- インストールバージョン確認
  docker version
```

## 起動手順

```
$ systemctl start docker
$ git clone https://github.com/oshou/dockerfiles
$ cd dockerfiles/lemp-stack-php74
$ export SRC_DIR=/path/to/your_application_directory
$ docker-compose up -d
```
