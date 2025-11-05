---
marp: true
theme: default
paginate: true
lang: ja
header: 'AI CLI Tools Kickstart Guide'
footer: '© 2025'
style: |
  section {
    font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
  }
  .icon {
    width: 64px;
    height: 64px;
    margin: 0 auto 20px;
    display: block;
  }
  .icon-small {
    width: 48px;
    height: 48px;
    display: inline-block;
    vertical-align: middle;
    margin-right: 10px;
  }
---

<!-- _class: title -->

# AI CLI Tools Kickstart Guide

生成AI界隈で話題のAI CLIツールについて
初学者向けに説明・比較するキックオフ資料

---

## 目次

1. Claude Code
2. Codex CLI
3. Gemini CLI
4. Cursor CLI
5. GitHub Copilot CLI
6. その他のAI CLIツール
7. 比較とまとめ

---

<!-- _class: split -->

## 🤖 Claude Code

<div style="text-align: center; margin-bottom: 20px;">
  <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="12" cy="12" r="10" fill="#D97757"/>
    <path d="M12 6L15 12L12 18L9 12Z" fill="white"/>
  </svg>
</div>

### 概要・特徴

Anthropicが開発したAIコーディングエージェント

- ✨ 自然言語によるコード生成・編集
- 🏠 ローカル環境での動作
- 📁 プロジェクト全体のコンテキスト理解
- 🔗 GitHub統合、エージェント型コーディング

### インストール方法

```bash
# npm経由でインストール
npm install -g @anthropic-ai/claude-code

# 認証（初回のみ）
claude login

# バージョン確認
claude --version
```

### 基本的な使い方

```bash
# インタラクティブモード
claude

# コマンドラインから直接実行
claude "タスクの説明"

# プロジェクト全体をコンテキストに含める
claude --project "機能を追加して"
```

### コスト

- 💰 Pro: $20/月
- 💎 Max: $100-200/月

---

<!-- _class: split -->

## 🧠 Codex CLI

<div style="text-align: center; margin-bottom: 20px;">
  <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 2L2 7L12 12L22 7L12 2Z" fill="#10A37F"/>
    <path d="M2 17L12 22L22 17M2 12L12 17L22 12" stroke="#10A37F" stroke-width="2" fill="none"/>
  </svg>
</div>

### 概要・特徴

OpenAIが開発したオープンソースのコーディングエージェント

- 💬 自然言語による直感的な操作
- 🔒 ローカル環境での動作（プライバシー保護）
- 🌍 多言語・多フレームワーク対応
- 🛡️ セキュリティ機能（サンドボックスモード）

### インストール方法

```bash
# macOS（Homebrew推奨）
brew install codex

# npm経由
npm install -g @openai/codex

# 認証設定
codex auth login

# 設定確認
codex --version
```

### 基本的な使い方

```bash
# 基本的な使用方法
codex "自然言語での指示"

# インタラクティブモード
codex --interactive

# 特定のファイルを編集
codex --file src/app.js "関数を追加"
```

### コスト

- 💳 ChatGPT Plus ($20/月) 以上で利用可能
- 🆓 Codex CLI自体は無料（API利用料が発生）

---

<!-- _class: split -->

## 💎 Gemini CLI

<div style="text-align: center; margin-bottom: 20px;">
  <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 2L2 7L12 12L22 7L12 2Z" fill="#4285F4"/>
    <circle cx="12" cy="17" r="5" fill="#34A853"/>
    <circle cx="12" cy="17" r="3" fill="#FBBC04"/>
  </svg>
</div>

### 概要・特徴

Googleが開発したAIコーディングエージェント

- 🚀 GoogleのGeminiモデルを活用
- 📝 自然言語によるコード生成
- ☁️ Google Cloudとの統合
- 📊 100万トークンのコンテキストウィンドウ
- 🎨 マルチモーダル対応、Web検索統合

### インストール方法

```bash
# npm経由でインストール
npm install -g @google/gemini-cli

# 初回起動時にGoogleアカウントで認証
gemini login

# APIキーの設定（オプション）
export GEMINI_API_KEY="your-api-key"

# バージョン確認
gemini --version
```

### 基本的な使い方

```bash
# インタラクティブモード
gemini

# コマンドラインから直接実行
gemini "タスクの説明"

# ファイルを指定して実行
gemini --file src/index.js "コードをリファクタリング"
```

### コスト

- 🆓 無料枠あり（毎分60回、1日1,000回）
- 💰 従量課金プランあり

---

<!-- _class: split -->

## ⚡ Cursor CLI

<div style="text-align: center; margin-bottom: 20px;">
  <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M3 3L21 21M21 3L3 21" stroke="#4A90E2" stroke-width="3" stroke-linecap="round"/>
    <circle cx="12" cy="12" r="8" stroke="#4A90E2" stroke-width="2" fill="none"/>
  </svg>
</div>

### 概要・特徴

Cursor IDEのコマンドラインインターフェース

- 🎯 インタラクティブモードと非対話モード
- 📋 セッション管理機能
- 🔌 MCP（Model Context Protocol）サポート
- ⚙️ ルールシステムによるカスタマイズ

### インストール方法

```bash
# 公式インストールスクリプト（推奨）
curl https://cursor.com/install -fsS | bash

# または手動インストール
# macOS
brew install cursor

# 認証（初回のみ）
cursor login

# 設定確認
cursor --version
```

### 基本的な使い方

```bash
# エージェントモード
cursor-agent "タスクの説明"

# インタラクティブモード
cursor-agent --interactive

# 特定のディレクトリで実行
cursor-agent --cwd ./project "機能を追加"
```

### コスト

- 🆓 現在ベータ版で無料
- 💰 正式リリース後の料金は未定

---

<!-- _class: split -->

## 🐙 GitHub Copilot CLI

<div style="text-align: center; margin-bottom: 20px;">
  <svg class="icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
    <circle cx="12" cy="12" r="10" fill="#24292F"/>
    <path d="M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM13 17H11V15H13V17ZM13 13H11V7H13V13Z" fill="white"/>
  </svg>
</div>

### 概要・特徴

GitHub Copilotのターミナル版

- 🔗 GitHubとの深い統合
- 🤖 エージェント機能
- 🔌 MCPによる拡張性
- 🔍 完全な制御と透明性

### インストール方法

```bash
# npm経由でインストール
npm install -g @github/copilot

# GitHub認証（初回のみ）
copilot auth login

# GitHub Copilotサブスクリプションが必要
# Copilot Pro ($10/月) または Copilot Business

# 設定確認
copilot --version
```

### 基本的な使い方

```bash
# インタラクティブモード
copilot

# プロンプトを指定して実行
copilot -p "プロンプト"

# エージェントモード
copilot agent "タスクの説明"

# GitHubリポジトリと連携
copilot --repo owner/repo "機能を追加"
```

### コスト

- 💳 Copilot Pro ($10/月) 以上で利用可能
- 🆓 CLI自体は追加料金なし

---

## 🛠️ その他のAI CLIツール

Claude Code、Codex CLI、Gemini CLI、Cursor CLI、GitHub Copilot CLI以外のAI特化型CLIツール

---

## ☁️ Amazon Q Developer CLI

**主な特徴**:
- 🔗 AWSサービスとの統合が強力
- 🤖 エージェント型のコーディング体験
- 🔧 運用のトラブルシューティング支援
- 📁 ローカルファイルの読み書きが可能

**主な機能**:
- 🤖 エージェント型コーディング体験
- ☁️ AWSリソースのクエリ
- 🐛 自動デバッグ
- 🔧 運用のトラブルシューティング支援

---

## 🚀 Grok CLI

**主な特徴**:
- 📦 オープンソース（MITライセンス）
- 💬 自然言語による直感的な操作
- 🧠 複数のAIモデルに対応
- ⚡ 導入が容易で学習コストが低い

**主な機能**:
- 💬 自然言語による操作
- 🧠 複数のAIモデル対応
- 📁 ファイル操作
- 💻 シェルコマンドの実行

```bash
# npm経由でインストール
npm install -g grok-cli

# またはPython経由
pip install grok-cli

# 認証設定
grok auth login

# 使用開始
grok "タスクの説明"
```

---

## 🤖 Cline

**主な特徴**:
- 🎯 自律型AIエージェント
- 🇯🇵 日本語対応
- 🔄 Git操作の自動化
- 📋 プロジェクト規約の定義が可能

**主な機能**:
- 💻 コード生成
- ✅ テスト作成
- 🔧 リファクタリング
- 📦 パッケージ管理
- 🔄 Git操作の自動化

**インストール方法**:
VS Code拡張機能としてインストール

```bash
# VS Code拡張機能マーケットプレイスから
# "Cline" を検索してインストール
```

---

## 🏭 Factory Droids

**主な特徴**:
- ⚡ 軽量・高速（GUI不要）
- 🔄 CI/CDパイプラインに統合可能
- 🤖 高い自動化能力
- 📊 Terminal-Benchで高い性能を記録（58.8%）

**主な機能**:
- 💬 自然言語によるコード生成
- 🔄 自動化
- 🚀 高性能処理

**インストール方法**:
```bash
npm install -g factory-droids
```

---

## scg-cli

**主な特徴**:
- セマンティックコードグラフの生成
- ポータブルなデータ形式（プロトコルバッファ）
- 外部ツールとの統合が容易
- ソフトウェア理解の支援

**主な機能**:
- コード解析
- セマンティックコードグラフの生成
- データエクスポート

Java/Scalaプロジェクト用のツール

---

## MLModelCI

**主な特徴**:
- モデルの最適化とテストの自動化
- クラウドデプロイメントの自動化
- オープンソース（Apache 2.0ライセンス）
- エラスティック評価のサポート

**主な機能**:
- モデルの最適化とテスト
- クラウドデプロイ
- プロファイリング
- エラスティック評価

```bash
pip install mlmodelci
```

---

## ShIOEnv

**主な特徴**:
- 文法誘導型のコマンド合成
- データセット作成の効率化
- 強化学習の適用
- オープンソース

**主な機能**:
- コマンド構築のマルコフ決定過程
- 文法誘導型サンプリング
- データセットの作成

CLI動作のキャプチャとデータセット生成

---

## i-Code Studio

**主な特徴**:
- マルチモーダルタスクの処理
- ファインチューニング不要
- 柔軟性と拡張性
- 複数モデルのオーケストレーション

**主な機能**:
- マルチモーダルタスクの実行
- モデルのオーケストレーション
- エージェントの構築

```bash
pip install icode-studio
```

---

## 📊 ツールの分類

### 💻 開発支援ツール
- ☁️ Amazon Q Developer CLI
- 🚀 Grok CLI
- 🤖 Cline
- 🏭 Factory Droids

### 🔍 コード解析ツール
- 📈 scg-cli

### 🧠 MLモデル管理ツール
- 🤖 MLModelCI

### 📚 データセット作成ツール
- 🔧 ShIOEnv

### 🎨 マルチモーダル処理ツール
- 🎯 i-Code Studio

---

## 比較表

| ツール名 | 主要機能 | 特徴 | 価格 | 対応OS | 備考 |
|---------|---------|------|------|--------|------|
| Claude Code | コード生成・編集・リファクタリング | AnthropicのClaudeモデル、エージェント型 | Pro: $20/月、Max: $100-200/月 | macOS, Linux, Windows(WSL) | GitHub統合、多言語対応 |
| Codex CLI | コード生成・編集・実行 | OpenAI、ローカル実行、サンドボックス | ChatGPT Plus($20)以上 | macOS, Linux, Windows(WSL) | オープンソース |
| Gemini CLI | コード生成・レビュー・Web検索 | Google Gemini、100万トークンコンテキスト | 無料枠あり、従量課金 | macOS, Linux, Windows(WSL) | オープンソース、マルチモーダル |
| Cursor CLI | コード生成・レビュー | IDE統合、MCPサポート | ベータ版（無料） | macOS, Linux, Windows(WSL) | Cursor IDEと統合 |
| GitHub Copilot CLI | コード生成・GitHub統合 | GitHubとの統合、エージェント機能 | Copilot Pro($10)以上 | macOS, Linux, Windows(WSL) | GitHub統合が強力 |

---

## まとめ

### 主要ツールの特徴

- **Codex CLI**: OpenAI、オープンソース、ローカル実行重視
- **Cursor CLI**: IDE統合、ベータ版で無料、MCPサポート
- **GitHub Copilot CLI**: GitHub統合が強力、エージェント機能

### 選択のポイント

- プロジェクトの要件や開発環境に応じて適切なツールを選択
- セキュリティ要件、コスト、統合の必要性を考慮
- 開発支援、コード解析、MLモデル管理など、用途に応じて使い分け

---

## 参考資料

各ツールの詳細情報は、以下のリンクから確認できます：

- [Claude Code](docs/claude-code/claude-code.md)
- [Codex](docs/codex/codex.md)
- [Gemini CLI](docs/gemini-cli/gemini-cli.md)
- [Cursor CLI](docs/cursor-cli/cursor-cli.md)
- [GitHub Copilot CLI](docs/github-copilot-cli/github-copilot-cli.md)
- [その他のAI CLIツール](docs/other-tools/other-tools.md)
- [比較表](docs/comparison.md)
- [参考資料](docs/references.md)

---

<!-- _class: title -->

# ご清聴ありがとうございました

質問・ご意見をお待ちしております

