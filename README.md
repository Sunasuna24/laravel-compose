# Laravelをインストールする方法

以下のLaravelアプリをコンテナから構築する方法を紹介します。

## githubからリポジトリをcloneする

```
git clone https://github.com/Sunasuna24/laravel-compose.git (任意のリポジトリ名)
```

## git管理を辞める

下記のコマンドを実行して、git管理を辞める。

```
rm -rf .git
```

## [WIP]M1チップに対応する

docker-compose.ymlにM1チップに対応するための以下のコードを追記する。

```
platform: linux/amd64
```

これは[このissue](https://github.com/Sunasuna24/laravel-prepare/issues/1)で対応予定。

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
