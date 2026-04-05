# Kong (Kubernetes Ingress Controller)

## 基本概念
| 用語 | 説明 |
|---|---|
| Service | バックエンドのアプリケーション |
| Route | リクエストを Service に振り分けるルール |
| Plugin | 認証・レート制限等の機能拡張 |
| Consumer | API を利用するユーザー/アプリ |
| Upstream | ロードバランシング対象のバックエンド群 |

## KongIngress / Ingress 設定

### 基本的な Ingress
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
  annotations:
    konghq.com/strip-path: "true"
spec:
  ingressClassName: kong
  rules:
  - http:
      paths:
      - path: /api
        pathType: Prefix
        backend:
          service:
            name: my-service
            port:
              number: 80
```

## プラグイン

### KongPlugin リソース
```yaml
apiVersion: configuration.konghq.com/v1
kind: KongPlugin
metadata:
  name: my-plugin
plugin: <plugin-name>
config:
  key: value
```

Service/Route に適用:
```yaml
metadata:
  annotations:
    konghq.com/plugins: my-plugin
```

### JWT 認証
```yaml
apiVersion: configuration.konghq.com/v1
kind: KongPlugin
metadata:
  name: jwt-auth
plugin: jwt
```

Consumer + credential:
```yaml
apiVersion: configuration.konghq.com/v1
kind: KongConsumer
metadata:
  name: my-user
  annotations:
    kubernetes.io/ingress.class: kong
username: my-user
---
apiVersion: configuration.konghq.com/v1
kind: KongConsumerGroup
metadata:
  name: jwt-credential
credentials:
- my-jwt-secret
```

### Rate Limiting
```yaml
apiVersion: configuration.konghq.com/v1
kind: KongPlugin
metadata:
  name: rate-limit
plugin: rate-limiting
config:
  minute: 60
  policy: local
```

### カナリアリリース
```yaml
apiVersion: configuration.konghq.com/v1
kind: KongPlugin
metadata:
  name: canary
plugin: canary
config:
  percentage: 10
  upstream_host: canary-service
  upstream_port: 80
```

## ロードバランシング

### 複数バックエンドへの振り分け
Ingress で weight を指定:
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: weighted
  annotations:
    konghq.com/strip-path: "true"
spec:
  ingressClassName: kong
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: service-v1
            port:
              number: 80
```

## Admin API (デバッグ用)
| コマンド | 説明 |
|---|---|
| `curl localhost:8001/` | Admin API ルート |
| `curl localhost:8001/services` | Service 一覧 |
| `curl localhost:8001/routes` | Route 一覧 |
| `curl localhost:8001/plugins` | Plugin 一覧 |
| `curl localhost:8001/consumers` | Consumer 一覧 |
| `curl localhost:8001/upstreams` | Upstream 一覧 |

## よく使う annotations
| annotation | 説明 |
|---|---|
| `konghq.com/strip-path: "true"` | パスプレフィックスを除去 |
| `konghq.com/plugins: name1,name2` | プラグイン適用 |
| `konghq.com/protocols: https` | プロトコル指定 |
| `konghq.com/preserve-host: "true"` | Host ヘッダーを保持 |

## Helm インストール
```bash
helm repo add kong https://charts.konghq.com
helm repo update
helm install kong kong/ingress -n kong --create-namespace
```
