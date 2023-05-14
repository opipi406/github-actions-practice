# GitHub Actions CI練習用
GitHub ActionsのCI環境構築の練習兼備忘録

# 導入手順

## 1. Secretsに機密情報を設定
https://github.com/[ユーザー]/[リポジトリ]/settings/secrets/actions で以下のSecretsを設定する。
```
リポジトリページ > Settings > Secrets and variables の Actions 
```

| 変数名                     | 概要                                    |
| -------------------------- | --------------------------------------- |
| DEV_HOST                   | 開発サーバーのホスト名                  |
| DEV_PORT                   | 開発サーバーの接続ポート番号            |
| DEV_USER                   | 開発サーバーの接続ユーザー名            |
| DEV_SSH_PRIVATE_KEY        | 開発サーバー接続用のローカルのSSH秘密鍵 |
| PRODUCTION_HOST            | 本番サーバーのホスト名                  |
| PRODUCTION_PORT            | 本番サーバーの接続ポート番号            |
| PRODUCTION_USER            | 本番サーバーの接続ユーザー名            |
| PRODUCTION_SSH_PRIVATE_KEY | 本番サーバー接続用のローカルのSSH秘密鍵 |

<span style="color: red">※ エックスサーバー接続時はポート番号は`10022`になるので注意！</span>

## 2. Deploy Keyの設定
デプロイ先のサーバーにSSH接続し、`ssh-keygen`で認証鍵の生成を行う。  
生成したSSH公開鍵をリポジトリSettings画面の**Deploy Key**に設定する。  

https://github.com/[ユーザー]/[リポジトリ]/settings/keys でDeploy Keyを設定する。  
```
リポジトリページ > Settings > Security の Deploy Keys  
```

※ `Allow write access` はOFFでOK

# メモ
- `SSH_PRIVATE_KEY` はローカルでリモートサーバーに接続するために使用しているSSH秘密鍵を指定する。
