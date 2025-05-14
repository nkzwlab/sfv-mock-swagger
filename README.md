# OpenAPIモックサーバーの構成

このプロジェクトでは、Stoplight PrismとCaddyを使用して、OpenAPI定義(Swagger)に基づくモックAPIサーバーを提供しています。

# 使い方

`swagger.yaml`のAPI定義を書き換えて，git commit & pushすれば自動で`https://xr-mock.jn.sfc.keio.ac.jp`が更新されるようになっています．
swaggerで調べたら大体書き方が乗ってます．何ならGUIベースでswaggerのyamlを出してくれるのもあります．
MQTTと違って，**swagger.yamlは全員で共有のもの**なので，勝手に人のエンドポイントを書き換えたり削除しないこと！conflictしたらslackでaskしてください．
githubのページに赤い×が出てたらビルド失敗してるのでask dang0

以下，copilotに出させたREADME(読まなくても支障はない)
## 概要

- `swagger.yaml`に定義されたAPIエンドポイントをモック化
- CaddyでHTTPS対応と自動証明書取得
- GitHubからの自動デプロイ機能

## システム構成

- **Prism**: OpenAPI定義からモックサーバーを生成（ポート4010）
- **Caddy**: リバースプロキシ、HTTPS対応、証明書自動管理

## APIエンドポイント例

- `GET /ping`: 簡単な疎通確認用エンドポイント
- `GET /users`: ユーザー一覧の取得
- `POST /users`: 新規ユーザーの作成