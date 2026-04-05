# docker compose

## 基本操作
| コマンド | 説明 |
|---|---|
| `docker compose up` | 全サービス起動 |
| `docker compose up -d` | バックグラウンド起動 |
| `docker compose up --build` | ビルドしてから起動 |
| `docker compose down` | 全サービス停止・削除 |
| `docker compose down -v` | ボリュームも含めて削除 |
| `docker compose stop` | 停止（コンテナは残る） |
| `docker compose start` | 停止したサービスを再開 |
| `docker compose restart` | 再起動 |

## 状態確認
| コマンド | 説明 |
|---|---|
| `docker compose ps` | サービス一覧 |
| `docker compose logs` | 全サービスのログ |
| `docker compose logs -f <service>` | 特定サービスのログをリアルタイム表示 |
| `docker compose top` | プロセス一覧 |

## サービス操作
| コマンド | 説明 |
|---|---|
| `docker compose up -d <service>` | 特定サービスだけ起動 |
| `docker compose exec <service> bash` | サービスに入る |
| `docker compose run <service> <cmd>` | 一時コンテナでコマンド実行 |
| `docker compose pull` | イメージを最新に更新 |

## ビルド
| コマンド | 説明 |
|---|---|
| `docker compose build` | 全サービスビルド |
| `docker compose build --no-cache` | キャッシュなしでビルド |
| `docker compose build <service>` | 特定サービスだけビルド |
