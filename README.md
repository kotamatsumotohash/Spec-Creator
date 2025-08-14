# au PAY In-App Wallet 仕様書・エージェントドキュメント

au PAY統合型暗号資産ウォレットの製品仕様書とAIエージェント定義を管理するリポジトリです。

## 📖 概要

このリポジトリには以下が含まれています：

- **製品仕様書**: au PAY In-App Walletの詳細な仕様
- **AIエージェント定義**: 開発・マネジメント・UX調査などの役割別エージェント
- **技術仕様**: 暗号資産からau PAY残高チャージの仕様など

## 🗂️ ファイル構成

```
├── CLAUDE.md              # メイン製品仕様書（Claude Code用プロジェクト設定）
├── README.md              # このファイル
├── .claude/               # Claude Code設定
│   └── commands/
│       └── spec-creator_v5.md  # 要求定義書作成コマンド
├── agents/                # AIエージェント定義
│   ├── developer.md       # 開発者エージェント
│   ├── manager.md         # マネージャーエージェント
│   ├── responsible.md     # 責任者エージェント
│   └── ux-researcher.md   # UXリサーチャーエージェント
├── spec/                  # 詳細仕様書
│   ├── column.md          # コラム・補足情報
│   └── crypto_to_auPAY_20250814.md  # 暗号資産→au PAY仕様
└── old/                   # 過去バージョン
    ├── spec-creator_v1.md
    ├── spec-creator_v2.md
    ├── spec-creator_v3.md
    └── spec-creator_v4.md
```

## 🚀 使い方

### 1. リポジトリのクローン（初心者向け）

**Git初心者の方**：

1. GitHubアカウントを作成（未作成の場合）
2. 以下のコマンドでリポジトリをダウンロード：

```bash
# このリポジトリをローカルにダウンロード
git clone https://github.com/kotamatsumotohash/au-pay-wallet-spec.git

# フォルダに移動
cd au-pay-wallet-spec
```

### 2. Claude Codeで開く（推奨）

**Claude Code初心者の方**：

1. Claude Codeをインストール：
```bash
# macOSの場合
brew install claude-code

# その他のインストール方法：https://docs.anthropic.com/en/docs/claude-code
```

2. このプロジェクトを開く：
```bash
# プロジェクトフォルダで実行
claude
```

3. Claude Codeが起動したら、以下のコマンドが使えます：
   - `/help` - ヘルプを表示
   - `/read CLAUDE.md` - メイン仕様書を読む
   - `/search キーワード` - ファイル内検索
   - `/spec-creator_v5` - 新機能の要求定義書を作成

### 3. ファイルの編集・更新

**基本的なGitワークフロー**：

```bash
# 1. 最新版を取得
git pull origin main

# 2. ファイルを編集（エディタで編集）

# 3. 変更を確認
git status

# 4. 変更をステージング
git add .

# 5. コミット（変更を記録）
git commit -m "変更内容の説明"

# 6. リモートリポジトリに送信
git push origin main
```

## ⚙️ 新機能の要求定義書作成

### `/spec-creator_v5` コマンドの使い方

au PAYウォレットに関する新機能の要求定義書を作成できます。Claude Code内で以下のコマンドを実行してください：

```bash
/spec-creator_v5
```

### 作成プロセス

`/spec-creator_v5`は4つのAIエージェントが連携して高品質な要求定義書を作成します：

1. **責任者エージェント（Responsible）**
   - ユーザーから要求をヒアリング
   - 要求定義書の初回ドラフトを作成
   - 各レビューフィードバックを反映

2. **UXリサーチャーエージェント（UX Researcher）** 
   - ユーザー体験の観点でレビュー
   - ペルソナ、フロー、アクセシビリティをチェック
   - UI状態（空・エラー・ローディング）の確認

3. **開発者エージェント（Developer）**
   - 技術的実現性をレビュー  
   - 依存関係、API設計、非機能要件をチェック
   - テスト可能性と観測性を確認

4. **マネージャーエージェント（Manager）**
   - 戦略整合性とビジネス価値をレビュー
   - コスト・リスク・スケジュールを評価
   - 最終承認とファイル生成

### 作成される成果物

- **ファイル名**: `./spec/<機能名>_要件定義_<YYYYMMDD>.md`
- **内容**: 
  - 概要・ビジネスゴール・KPI
  - 想定ユーザーフロー・UI仕様
  - 機能要求（Must/Should/Could/Won't優先度）
  - 運用・セキュリティ・コンプライアンス要件
  - 開発チームへの引き継ぎ事項

### 使用例

```bash
# Claude Code起動後
/spec-creator_v5

# エージェントが以下を質問します：
# 1. 機能の概要
# 2. 目的・ゴール  
# 3. 想定ユーザーフロー
# 4. 補足情報

# 回答後、4つのエージェントが順次レビューし、
# 最終的にspec/フォルダに要求定義書が生成されます
```

## 🤖 AIエージェントシステム

### agentsフォルダについて

各エージェントの役割と責任が定義されています：

| エージェント | ファイル | 主な責任 |
|-------------|---------|----------|
| **責任者** | `responsible.md` | 要求収集、ドラフト作成、テンプレート遵守 |
| **UXリサーチャー** | `ux-researcher.md` | ユーザー体験、フロー設計、アクセシビリティ |
| **開発者** | `developer.md` | 技術実現性、API設計、非機能要件 |
| **マネージャー** | `manager.md` | 戦略整合性、リスク管理、最終承認 |

### エージェントの特徴

- **多言語対応**: 内部では英語で思考、出力は日本語
- **専門性**: 各エージェントが専門領域に特化
- **連携**: ステップ式でレビューを重ね、品質を向上
- **テンプレート準拠**: 一貫した文書構造を保証

## 📋 主要な仕様項目

### 製品概要
- **コンセプト**: Pontaポイントで暗号資産を購入できるau PAY統合ウォレット
- **ターゲット**: 暗号資産初心者、au PAYユーザー
- **キー機能**: ポイント交換、マルチチェーン対応、WalletConnect

### 技術仕様
- **対応チェーン**: Ethereum, Polygon, Base, Aptos, Oasys
- **対応トークン**: CoinGecko対応FT、ERC721/ERC1155 NFT
- **セキュリティ**: KDDI基準、Safe Site フィルタリング

詳細は [`CLAUDE.md`](./CLAUDE.md) をご確認ください。

## 🤝 貢献方法

1. このリポジトリをフォーク
2. 新しいブランチを作成：`git checkout -b feature/新機能名`
3. 変更をコミット：`git commit -m "新機能: 説明"`
4. ブランチをプッシュ：`git push origin feature/新機能名`
5. プルリクエストを作成

## 📝 ライセンス

このプロジェクトは内部仕様書のため、社内利用に限定されます。

## 📞 サポート

- **Claude Codeヘルプ**: `/help` または [公式ドキュメント](https://docs.anthropic.com/en/docs/claude-code)
- **Gitヘルプ**: [Git基本コマンド](https://git-scm.com/docs)
- **問題報告**: GitHubのIssuesタブから報告

---

**初心者Tips** 💡
- `CLAUDE.md`がメインファイルです。まずここから読み始めましょう
- Claude Codeを使えば、自然言語でファイルの内容を質問できます
- 新機能の要求定義書は`/spec-creator_v5`コマンドで簡単に作成できます
- 変更前は必ず`git pull`で最新版を取得しましょう
- エージェントが順次レビューするので、高品質な仕様書が自動生成されます