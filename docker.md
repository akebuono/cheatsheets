# docker

## コンテナ操作
| コマンド | 説明 |
|---|---|
| `docker run <image>` | コンテナ起動 |
| `docker run -d <image>` | バックグラウンド起動 |
| `docker run -it <image> bash` | 対話的に起動 |
| `docker run -p 8080:80 <image>` | ポートマッピング |
| `docker run -v $(pwd):/app <image>` | ボリュームマウント |
| `docker ps` | 実行中コンテナ一覧 |
| `docker ps -a` | 全コンテナ一覧（停止含む） |
| `docker stop <id>` | コンテナ停止 |
| `docker start <id>` | コンテナ再開 |
| `docker rm <id>` | コンテナ削除 |
| `docker rm -f <id>` | 強制削除 |
| `docker logs <id>` | ログ表示 |
| `docker logs -f <id>` | ログをリアルタイム表示 |
| `docker exec -it <id> bash` | 実行中コンテナに入る |
| `docker inspect <id>` | コンテナ詳細情報 |

## イメージ操作
| コマンド | 説明 |
|---|---|
| `docker images` | イメージ一覧 |
| `docker pull <image>` | イメージ取得 |
| `docker build -t <name> .` | イメージビルド |
| `docker rmi <image>` | イメージ削除 |
| `docker tag <src> <dst>` | タグ付け |
| `docker push <image>` | レジストリに push |

## ネットワーク
| コマンド | 説明 |
|---|---|
| `docker network ls` | ネットワーク一覧 |
| `docker network create <name>` | ネットワーク作成 |
| `docker network inspect <name>` | ネットワーク詳細 |

## ボリューム
| コマンド | 説明 |
|---|---|
| `docker volume ls` | ボリューム一覧 |
| `docker volume create <name>` | ボリューム作成 |
| `docker volume rm <name>` | ボリューム削除 |

## クリーンアップ
| コマンド | 説明 |
|---|---|
| `docker system prune` | 未使用リソース一括削除 |
| `docker system prune -a` | 未使用イメージも含めて削除 |
| `docker system df` | ディスク使用量確認 |
