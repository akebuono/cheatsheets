# Kiro CLI

## 起動
| コマンド | 説明 |
|---|---|
| `kiro-cli chat` | チャット開始 |
| `kiro-cli chat --resume` | 前回の会話を再開 |
| `kiro-cli chat --resume-picker` | 会話を選んで再開 |
| `kiro-cli chat --agent <name>` | エージェント指定で開始 |
| `kiro-cli chat --trust-all-tools` | 全ツール自動承認 |
| `kiro-cli chat --no-interactive "query"` | ヘッドレスモード |

## キーボードショートカット
| キー | 操作 |
|---|---|
| `Ctrl+C` | 処理キャンセル / 終了 |
| `Ctrl+R` | コマンド履歴検索 |
| `Ctrl+T` | タンジェントモード切替 |
| `Ctrl+F` | ファジー検索 |
| `Ctrl+D` | デリゲートモード |
| `↑/↓` | コマンド履歴ナビゲーション |
| `Tab` | オートコンプリート |

## スラッシュコマンド — 会話管理
| コマンド | 説明 |
|---|---|
| `/chat save <path>` | 会話をファイルに保存 |
| `/chat load <path>` | 保存した会話を読み込み |
| `/chat new` | 新しい会話を開始 |
| `/chat new <prompt>` | プロンプト付きで新規開始 |
| `/clear` | 会話履歴をクリア |
| `/quit` (`/q`) | 終了 |

## スラッシュコマンド — エージェント・モデル
| コマンド | 説明 |
|---|---|
| `/agent` | エージェント切り替え |
| `/agent swap` | 特定エージェントに切替 |
| `/agent generate` | AI でエージェント生成 |
| `/model` | モデル切り替え |

## スラッシュコマンド — ツール・コンテキスト
| コマンド | 説明 |
|---|---|
| `/tools` | 利用可能なツール一覧 |
| `/tools trust <name>` | ツールを信頼（確認不要に） |
| `/tools trust-all` | 全ツールを信頼 |
| `/tools reset` | 権限をリセット |
| `/context` | コンテキストファイル管理 |
| `/mcp` | MCP サーバー管理 |

## スラッシュコマンド — その他
| コマンド | 説明 |
|---|---|
| `/help` | ヘルプエージェントに切替 |
| `/help --legacy` | コマンド一覧表示 |
| `/tangent` | タンジェントモード（脱線用） |
| `/tangent tail` | 最後のQ&Aを残して戻る |
| `/tangent forget [n]` | 直近n件のメッセージを削除 |
| `/prompts list` | プロンプト一覧 |
| `/prompts get <name>` | プロンプト使用 |
| `/knowledge show` | ナレッジベース一覧 |
| `/knowledge add` | ナレッジ追加 |
| `/editor` | エディタでプロンプト作成 |

## タンジェントモード
脱線して質問 → 元の会話に戻れる機能。
1. `/tangent` で脱線モードに入る（プロンプトに `↯` 表示）
2. 質問する
3. `/tangent` で元の会話に復帰

## 設定
```bash
kiro-cli settings <key> <value>     # 設定変更
kiro-cli settings <key>             # 現在値確認
kiro-cli settings --delete <key>    # 設定削除
```

## エージェント管理
```bash
kiro-cli agent list                 # エージェント一覧
kiro-cli agent create --name <name> # エージェント作成
kiro-cli agent validate <name>      # 設定の検証
```

エージェント設定ファイル:
- ローカル: `.kiro/agents/<name>.json`
- グローバル: `~/.kiro/agents/<name>.json`
