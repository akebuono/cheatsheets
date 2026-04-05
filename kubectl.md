# kubectl

## コンテキスト・設定
| コマンド | 説明 |
|---|---|
| `kubectl config get-contexts` | コンテキスト一覧 |
| `kubectl config use-context <name>` | コンテキスト切り替え |
| `kubectl config current-context` | 現在のコンテキスト |
| `kubectl cluster-info` | クラスタ情報 |

## リソース確認
| コマンド | 説明 |
|---|---|
| `kubectl get pods` | Pod 一覧 |
| `kubectl get pods -A` | 全 namespace の Pod |
| `kubectl get svc` | Service 一覧 |
| `kubectl get deploy` | Deployment 一覧 |
| `kubectl get nodes` | Node 一覧 |
| `kubectl get all` | 主要リソース一覧 |
| `kubectl get <resource> -o wide` | 詳細付き一覧 |
| `kubectl get <resource> -o yaml` | YAML 出力 |

## 詳細・デバッグ
| コマンド | 説明 |
|---|---|
| `kubectl describe pod <name>` | Pod 詳細 |
| `kubectl logs <pod>` | ログ表示 |
| `kubectl logs -f <pod>` | ログをリアルタイム表示 |
| `kubectl logs <pod> -c <container>` | 特定コンテナのログ |
| `kubectl exec -it <pod> -- bash` | Pod に入る |
| `kubectl top pods` | Pod のリソース使用量 |
| `kubectl top nodes` | Node のリソース使用量 |

## リソース作成・更新
| コマンド | 説明 |
|---|---|
| `kubectl apply -f <file>` | マニフェスト適用 |
| `kubectl apply -f <dir>/` | ディレクトリ内を一括適用 |
| `kubectl create -f <file>` | リソース作成 |
| `kubectl delete -f <file>` | マニフェストのリソース削除 |
| `kubectl delete pod <name>` | Pod 削除 |

## スケール・ロールアウト
| コマンド | 説明 |
|---|---|
| `kubectl scale deploy <name> --replicas=3` | レプリカ数変更 |
| `kubectl rollout status deploy <name>` | ロールアウト状況 |
| `kubectl rollout history deploy <name>` | ロールアウト履歴 |
| `kubectl rollout undo deploy <name>` | ロールバック |

## ポートフォワード・コピー
| コマンド | 説明 |
|---|---|
| `kubectl port-forward <pod> 8080:80` | ポートフォワード |
| `kubectl port-forward svc/<name> 8080:80` | Service 経由 |
| `kubectl cp <pod>:/path ./local` | ファイルコピー |

## namespace
| コマンド | 説明 |
|---|---|
| `kubectl get ns` | namespace 一覧 |
| `kubectl -n <ns> get pods` | namespace 指定 |
| `kubectl create ns <name>` | namespace 作成 |
