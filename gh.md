# gh (GitHub CLI)

## 認証
| コマンド | 説明 |
|---|---|
| `gh auth login` | ログイン |
| `gh auth status` | 現在のアカウント確認 |
| `gh auth switch` | アカウント切り替え |
| `gh auth logout` | ログアウト |

## リポジトリ
| コマンド | 説明 |
|---|---|
| `gh repo create <name> --public` | 公開リポジトリ作成 |
| `gh repo create <name> --private` | 非公開リポジトリ作成 |
| `gh repo clone <owner/repo>` | クローン |
| `gh repo view` | リポジトリ情報表示 |
| `gh browse` | ブラウザで開く |

## Pull Request
| コマンド | 説明 |
|---|---|
| `gh pr create` | PR 作成 |
| `gh pr list` | PR 一覧 |
| `gh pr view <number>` | PR 詳細 |
| `gh pr checkout <number>` | PR のブランチに切り替え |
| `gh pr merge <number>` | PR マージ |

## Issue
| コマンド | 説明 |
|---|---|
| `gh issue create` | Issue 作成 |
| `gh issue list` | Issue 一覧 |
| `gh issue view <number>` | Issue 詳細 |
| `gh issue close <number>` | Issue クローズ |

## SSH keys
| コマンド | 説明 |
|---|---|
| `gh ssh-key list` | 登録済み SSH 鍵一覧 |
| `gh ssh-key add <file>` | SSH 鍵を追加 |
