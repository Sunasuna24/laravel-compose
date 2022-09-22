# Laravelをインストールする方法

## githubからリポジトリをcloneする

```
git clone https://github.com/Sunasuna24/laravel-compose.git
```

## リポジトリ名を変更する

```
$ mv laravel-compose 変更したい名前
```

## 必要に応じてDockerfileで使用するイメージを修正する

今はPHPが7.4-apacheというイメージを使用している。

## 【必須】000-default.confでディレクトリ名を変更する

サンプルでは`laraveltokyo`という名前になっているのを適宜変更する。

## 【必須】docker-compose.ymlでディレクトリ名を変更する

先ほどと同様に、docker-compose.ymlでもディレクトリ名を変更する。

- appのコンテナ名
    - laravel_app
- dbのコンテナ名
    - larave_db
- dbの各種設定
    - MYSQL_DATABASE: laravel_db
    - MYSQL_USER: laravel_user
    - MYSQL_PASSWORD: laravel_pass

## あとは立ち上げる

以下のコマンドを順次実行する

```
docker-compose build
docker-compose up -d
docker-compose exec app bash
composer create-project --prefer-dist laravel/laravel アプリ名 "バージョン数"
cd アプリ名
chmod 777 -R storage/
php artisan key:generate
```

## localhostで確認する

localhostで確認してみよう！
