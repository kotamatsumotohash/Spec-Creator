# au PAY Wallet 要求定義書作成エージェント

au PAY Wallet内の機能の要求定義書を作成するリポジトリです。

## 📖 概要

このリポジトリには以下が含まれています：

- **au PAY Wallet概要**: au PAY Walletの概要
- **AIエージェント定義**: 開発・マネジメント・UX調査などの役割別エージェント
- **コマンド**: AIエージェントを動かして要求定義書を作成するコマンド

## 🗂️ ファイル構成

```
├── CLAUDE.md              # au PAY Wallet概要（Claude Code起動時に自動読み込み）
├── README.md              # 本ファイル
├── .claude/               # Claude Code設定
│   └── commands/
│       └── spec-creator_v5.md  # 要求定義書作成コマンド定義
├── agents/                # AIエージェント定義
│   ├── developer.md       # 開発者エージェント
│   ├── manager.md         # マネージャーエージェント
│   ├── responsible.md     # 責任者エージェント
│   └── ux-researcher.md   # UXリサーチャーエージェント
└── spec/                  # 作成した要求定義書

```

### 重要なファイルの説明

**CLAUDE.md**：
- Claude Codeが起動時に自動的に読み込む製品仕様書
- au PAY Walletの概要、機能要件、技術仕様が英語で記載
- AIエージェントがこの内容を基に要求定義書を作成

**.claude/commands/spec-creator_v5.md**：
- カスタムコマンド `/spec-creator_v5` の定義ファイル
- 4つのAIエージェント（responsible.md, ux-researcher.md, developer.md, manager.md）を順次呼び出すワークフローを定義
- `agents/` フォルダ内のエージェント定義ファイルを参照して動作

**agents/ フォルダ**：
- 各AIエージェントの役割、専門性、出力形式が定義
- コマンドファイルから参照され、専門的なレビューと要求定義書作成を実行

## 🚀 セットアップ

### 1. リポジトリのクローン

**方法A: Gitを使う場合**：

1. GitHubアカウントを作成（未作成の場合）
2. Gitをインストール：
   - **Windows**: [Git for Windows](https://gitforwindows.org/)をダウンロード・インストール
   - **Mac**: 
     - Homebrewがある場合: `brew install git`
     - Homebrewがない場合: [Git公式サイト](https://git-scm.com/download/mac)からインストーラーをダウンロード
   - **Linux**: `sudo apt install git`（Ubuntu/Debian）または `sudo yum install git`（CentOS/RHEL）
3. 以下のコマンドでリポジトリをダウンロード：

```bash
# このリポジトリをローカルにダウンロード
git clone https://github.com/kotamatsumotohash/au-pay-wallet-spec.git

# フォルダに移動
cd au-pay-wallet-spec
```

**方法B: Gitなしの場合**：

1. [リポジトリページ](https://github.com/kotamatsumotohash/au-pay-wallet-spec)にアクセス
2. 緑の「Code」ボタンをクリック
3. 「Download ZIP」を選択してファイルをダウンロード
4. ZIPファイルを解凍
5. 解凍したフォルダに移動

**注意**: ZIP形式でダウンロードした場合、変更を元のリポジトリに反映するにはGitの知識が必要になります。継続的に使用する場合は方法Aを推奨します。

### 2. Claude Codeで開く

**Claude Code初心者の方**：

1. Claude Codeをインストール：
```bash
# macOSでHomebrewがある場合
brew install claude-code

# macOSでHomebrewがない場合、またはその他のOS
インストール方法：https://docs.anthropic.com/en/docs/claude-code
```

2. このプロジェクトを開く：
```bash
# プロジェクトフォルダで実行
claude
```

3. Claude Codeが起動したら、以下のコマンドなどが使えます：
   - `/help` - ヘルプを表示
   - `/read CLAUDE.md` - メイン仕様書を読む
   - `/search キーワード` - ファイル内検索
   - `/spec-creator_v5` - 新機能の要求定義書を作成


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

- **ファイル名**: `./spec/<機能名>_<YYYYMMDD>.md`
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

### au PAY Wallet概要
- **コンセプト**: Pontaポイントで暗号資産を購入できるau PAY Wallet
- **ターゲット**: 暗号資産初心者、au PAYユーザー
- **キー機能**: ポイント交換、マルチチェーン対応、WalletConnect

### 技術仕様
- **対応チェーン**: Ethereum, Polygon, Base, Aptos, Oasys
- **対応トークン**: CoinGecko対応FT、ERC721/ERC1155 NFT
- **セキュリティ**: KDDI基準、安全サイトフィルタリング

詳細は [`CLAUDE.md`](./CLAUDE.md) をご確認ください。

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