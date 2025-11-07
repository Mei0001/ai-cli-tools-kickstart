---
marp: true
theme: default
paginate: true
lang: ja
header: 'AI CLI Tools Kickstart Guide'
footer: '© 2025'
size: 16:9
style: |
  section {
    font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
    font-size: 20px;
    padding: 35px 50px;
    overflow: hidden;
  }
  h1 {
    font-size: 40px;
    margin-bottom: 15px;
    line-height: 1.2;
  }
  h2 {
    font-size: 30px;
    margin-top: 15px;
    margin-bottom: 12px;
    line-height: 1.3;
  }
  h3 {
    font-size: 24px;
    margin-top: 12px;
    margin-bottom: 8px;
    line-height: 1.3;
  }
  p, li {
    font-size: 17px;
    line-height: 1.4;
    margin-bottom: 8px;
  }
  ul, ol {
    margin-top: 8px;
    margin-bottom: 8px;
  }
  code {
    font-size: 18px;
    padding: 2px 6px;
  }
  pre {
    font-size: 18px;
    padding: 12px;
    max-height: 350px;
    overflow-x: auto;
    overflow-y: auto;
    line-height: 1.4;
    margin: 8px 0;
    white-space: pre;
    word-wrap: normal;
    overflow-wrap: normal;
  }
  pre code {
    font-size: 18px;
    padding: 0;
  }
  table {
    font-size: 13px;
    margin: 8px 0;
    width: 100%;
    border-collapse: collapse;
    table-layout: auto;
  }
  th, td {
    padding: 5px 7px;
    font-size: 13px;
    word-wrap: break-word;
    max-width: 200px;
  }
  .icon {
    width: 80px;
    height: 80px;
    margin: 0 auto 15px;
    display: block;
  }
  .icon-small {
    width: 40px;
    height: 40px;
    display: inline-block;
    vertical-align: middle;
    margin-right: 8px;
  }
  .feature-list {
    font-size: 18px;
    line-height: 1.6;
  }
  .feature-list li {
    margin-bottom: 8px;
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

## 🤖 Claude Code

<div style="text-align: center; margin-bottom: 15px;">
  <img src="assets/images/claude-logo.svg" alt="Claude Logo" style="width: 100px; height: 100px;">
</div>

### 概要

Anthropic社が開発したエージェント型のAIコーディング支援ツール

- **自然言語による指示**でコードの生成、編集、デバッグ、リファクタリングを自律的に実行
- **多言語対応**: JavaScript/TypeScript、Python、Java、C++、Go、Rust、PHP、Ruby、HTML/CSS、SQL、シェルスクリプトなど
- **GitHub統合**: GitHub Actionsと連携し、CI/CDパイプラインの自動化をサポート
- **プロジェクト全体の理解**: プロジェクト全体を読み込み、構成や機能を解析

---

## Claude Code - 主な特徴

### エージェント型コーディング
- 自然言語での指示に基づき、コードの生成、修正、リファクタリング、テスト実行などを自律的に実行
- 複数のステップからなるタスクを自律的に計画・実行

### 対話型インターフェース
- ターミナル上での自然言語による対話を通じて、段階的に作業を進めることが可能
- 通常モード、auto-acceptモード、planモードを選択可能

### 高度な機能
- **カスタムスラッシュコマンド**: ユーザーが独自のコマンドを定義
- **サブエージェント**: 特定の機能やタスクに特化したエージェントを作成
- **MCP連携**: GitHub、Notion、Backlogなどのツールと連携

---

## Claude Code - システム要件・インストール

### システム要件
- **OS**: macOS 10.15以降、Ubuntu 20.04+/Debian 10+、Windows 10+（WSL推奨）
- **Node.js**: 18以上
- **RAM**: 4GB以上
- **アカウント**: ProまたはMaxプランのサブスクリプションが必要

### インストール方法

```bash
# npm経由でインストール（sudoは非推奨）
npm install -g @anthropic-ai/claude-code

# バージョン確認
claude --version

# 認証（初回のみ）
claude login
# または単に
claude
```

### プロジェクトの初期化（オプション）

```bash
claude init
```

---

## Claude Code - 基本的な使い方

### インタラクティブモード

```bash
# 対話型セッションを開始
claude

# 初期プロンプトを指定して開始
claude "認証モジュールをJWTトークンを用いるようにリファクタリングして"
```

### コマンド機能

- `/cost`: 現在のセッションの使用量を確認
- `/clear`: 会話履歴をクリア
- `/plan`: 計画モードに切り替え
- `/mcp`: MCPサーバーの管理
- `/reviewit`: コードレビュー機能

### モード切り替え

- **通常モード**: 各ステップで確認を求めながら作業を進める
- **auto-acceptモード**: 自動的にステップを承認（`Shift+Tab`で切り替え）
- **planモード**: 実行前に計画を立てて確認（`Shift+Tab`で切り替え）

---

## Claude Code - コスト

### サブスクリプションプラン

| プラン | 料金 | モデル | 用途 |
|--------|------|--------|------|
| **Pro** | $20/月（年払い$17/月） | Sonnet 4.5 | 小規模なコードベース、約45回/5時間 |
| **Max 5x** | $100/月 | Sonnet 4.5 + Opus 4.1 | 大規模コードベース、約225回/5時間 |
| **Max 20x** | $200/月 | Sonnet 4.5 + Opus 4.1 | 大規模コードベース、約900回/5時間 |
| **Team** | $150/ユーザー/月（最低5人） | Sonnet 4.5 + Opus 4.1 | チーム管理機能付き |
| **Enterprise** | 要問い合わせ | Sonnet 4.5 + Opus 4.1 | 高度なセキュリティ・データ管理 |

### コスト管理
- 平均的なコスト: 開発者1人あたり1日約$6程度
- ユーザーの90%は1日$12未満で利用
- `/cost`コマンドで使用量を確認可能

---

## Claude Code - 得意なこと・苦手なこと

### ✅ 得意なこと

- **コードの自動生成と編集**: 要件を伝えるだけで適切なコード構造を提案・生成
- **コードレビュー**: コミット差分を解析し、自動でレビューコメントや改善提案を生成
- **CI/CD支援**: DockerfileやGitHub ActionsのYAMLを自動生成
- **リファクタリング**: コードの品質向上のためのリファクタリング提案を自動実行
- **テスト生成**: コードに対するテストケースを自動生成
- **デバッグ支援**: エラーメッセージの解析やバグの特定を支援

### ❌ 苦手なこと

- **大規模で複雑なコードベースの処理**: プロジェクト全体の文脈を完全に理解するのは難しい場合がある
- **セキュリティ関連のコード**: 認証・認可周りのコードは必ず人間がレビューが必要
- **パフォーマンスクリティカルな処理**: N+1クエリやメモリリークを引き起こすコードを生成する可能性
- **創造的な設計**: 新規性の高いアルゴリズムや設計の創出は得意ではない

---

## 🧠 Codex CLI

<div style="text-align: center; margin-bottom: 15px;">
  <img src="assets/images/openai-logo.svg" alt="OpenAI Codex Logo" style="width: 100px; height: 100px;">
</div>

### 概要

OpenAIが開発したオープンソースのコーディングエージェント

- **自然言語による直感的な操作**: リポジトリ内を移動し、ファイルの編集やコマンドの実行、テストの実施などを自律的に実行
- **ローカル環境での動作**: ソースコード自体はOpenAI側に送信されず、プライバシーが保護される
- **多言語・多フレームワーク対応**: 複数のプログラミング言語やフレームワークをサポート
- **セキュリティ機能**: サンドボックス環境を提供し、安全なコード実行をサポート

---

## Codex CLI - 主な特徴

### 自然言語による直感的な操作
- 自然言語で指示を出すだけで、Codexがリポジトリ内を移動し、ファイルの編集やコマンドの実行、テストの実施などを行います
- コード生成、レビュー、デバッグ、説明など、多様な開発タスクに対応

### セキュリティとプライバシー
- **ローカル環境での動作**: ソースコード自体はOpenAI側に送信されません。送信されるのはプロンプトや差分のサマリーのみ
- **安全なサンドボックス環境**: コードの安全な実行環境を提供し、作業領域への書き込みをサポートしつつ、デフォルトでインターネットアクセスを制限
- `--full-auto`モードでは、ネットワークアクセスを遮断した仮想環境内でコードを実行

### 柔軟なカスタマイズ
- TOML形式の設定ファイルを使用し、複数のプロバイダー設定やプロファイルの迅速な切り替えが可能
- ホームディレクトリに`.codex/AGENTS.md`ファイルを作成し、個別の指示や設定を記述することで、Codex CLIの動作をカスタマイズ可能

---

## Codex CLI - システム要件・インストール

### システム要件
- **OS**: macOS 12以上、Ubuntu 20.04+/Debian 10+、Windows 11（WSL2経由）
- **Node.js**: バージョン22以上（LTSバージョン推奨）
- **Git**: バージョン2.23以上
- **RAM**: 最低4GB、推奨8GB以上
- **OpenAI APIキー**: OpenAIのウェブサイトから取得

### インストール方法（macOS）

```bash
# 方法1: Homebrewを使用（推奨）
brew install codex

# 方法2: npmを使用
npm install -g @openai/codex

# バージョン確認
codex --version

# 初回起動と認証
codex
# 初回起動時には、ChatGPTアカウントでのサインインが求められます
```

### APIキーの設定（ChatGPTプランを使用しない場合）

```bash
# zshを使用している場合
echo 'export OPENAI_API_KEY="your-api-key-here"' >> ~/.zshrc
source ~/.zshrc
```

---

## Codex CLI - 基本的な使い方

### 基本的なコマンド形式

```bash
codex "自然言語での指示"
```

### コード生成

```bash
# SQLテーブルの作成
codex "ユーザーテーブルを作成するSQLを書いて"

# Python関数の生成
codex "リストから重複を削除するPython関数を作成して"

# Reactコンポーネントの生成
codex "ボタンコンポーネントをReactで作成して"
```

### コード編集・リファクタリング

```bash
# ReactクラスコンポーネントをHooksに変換
codex "ReactクラスコンポーネントをHooksに変換して"

# コードの最適化
codex "このファイルのパフォーマンスを最適化して"
```

### サンドボックスモード

```bash
# ネットワークアクセスを遮断した安全な環境でコードを実行
codex --full-auto "このスクリプトを実行して"
```

---

## Codex CLI - コスト

### Codex CLI自体の費用
- **Codex CLI自体はオープンソースで無料**で利用できます
- 実際に使用するにはOpenAIのAPIを利用するため、API利用料が発生します

### ChatGPTプラン経由での利用

| プラン | 月額料金 | Codex利用 | 初期クレジット |
|--------|----------|-----------|----------------|
| Free | 無料 | ❌ 利用不可 | - |
| Plus | $20 | ✅ 利用可能 | $5相当 |
| Pro | $200 | ✅ 優先アクセス | $50相当 |
| Team | 契約制 | ✅ 利用可能 | - |
| Enterprise | 契約制 | ✅ 利用可能 | - |

### API直接利用時の料金（2025年時点）

| モデル | 入力トークン | 出力トークン |
|--------|--------------|--------------|
| o3 | $0.06/1K | $0.24/1K |
| o4-mini | $0.01/1K | $0.04/1K |
| codex-mini | $0.003/1K | $0.012/1K |

---

## Codex CLI - 得意なこと・苦手なこと

### ✅ 得意なこと

- **新規機能開発**: 自然言語で新しい機能の要件を伝えるだけで、関連ファイルのコードを自動生成
- **バグ修正**: エラーレポートやデバッグログを基に、問題のある箇所を特定し、適切な修正案を提案・適用
- **リファクタリング**: 開発中のコードを分析し、潜在的な問題点や改善点を指摘
- **テスト自動化**: テストコードの生成や実行を支援
- **コードの説明**: 既存のコードの動作や目的を説明することができます
- **シェルコマンドの実行**: 自然言語の指示から適切なシェルコマンドを生成し、実行

### ❌ 苦手なこと

- **複雑なプロジェクトの全体的な理解**: 大規模で複雑なプロジェクト全体の文脈を完全に把握するのは難しい場合がある
- **多ステップの大規模変更**: 複数ファイルにまたがる修正やビジネスロジックの変更には、人間の監督が必要
- **最新のライブラリやフレームワークへの対応**: 新しく登場したライブラリやフレームワークに対する知識が不足している場合がある
- **複雑な判断を要するリファクタリング**: ルーチン作業には強いが、複雑な判断を要するリファクタリングには人間の判断が必要

---

## 💎 Gemini CLI

<div style="text-align: center; margin-bottom: 15px;">
  <img src="assets/images/gemini-logo.svg" alt="Google Gemini Logo" style="width: 100px; height: 100px;">
</div>

### 概要

Googleが2025年6月に発表したオープンソースのAIエージェントツール

- **大規模コンテキスト処理**: 最大100万トークンのコンテキストウィンドウを持ち、複雑なコードベースの理解や編集が可能
- **マルチモーダル対応**: テキストだけでなく、画像やPDFなどの多様な入力形式を処理
- **ReActループの採用**: 「思考→ツール実行→回答生成」というステップを繰り返し、複雑なタスクを効率的に処理
- **Google検索との統合**: リアルタイムでウェブから情報を取得し、外部コンテキストをモデルに提供
- **MCP（Model Context Protocol）対応**: 外部ツールとの柔軟な連携が可能
- **オープンソース**: 完全オープンソースで提供され、カスタマイズや拡張が容易

---

## Gemini CLI - 主な特徴

### 大規模コードベースのサポート
- 100万トークン以上のコンテキストを処理でき、大規模なプロジェクトの分析が容易
- 複雑なリポジトリのアーキテクチャ把握が可能

### マルチモーダルアプリのプロトタイピング
- PDFやスケッチからアプリのプロトタイプを迅速に生成
- テキスト、画像、PDFなど多様な入力形式に対応

### DevOpsタスクの自動化
- Git操作、プルリクエストの取得、移行計画の作成などが可能
- 開発ワークフローの自動化を実現

### ツール統合
- MCPサーバーを介して、Imagen、Veo、Lyriaなどのメディア生成モデルに接続
- 組み込みのGoogle検索により、最新で信頼性の高い回答が得られる

---

## Gemini CLI - システム要件・インストール

### 前提条件
- **Node.js**: バージョン18以上が必要
- **OS**: macOS、Linux、Windows（WSL経由）に対応

### インストール方法（macOS）

```bash
# 方法1: npmを使用（推奨）
npm install -g @google/gemini-cli

# 方法2: npxを使用（一時的な実行）
npx @google/gemini-cli

# インストールの確認
gemini --version
```

### 認証方法

```bash
# 1. Googleアカウントでの認証（推奨・無料枠利用）
gemini
# テーマカラーを選択後、ブラウザが自動で起動し、Googleアカウントでログイン

# 2. APIキーの使用
export GEMINI_API_KEY="YOUR_API_KEY"

# 3. Vertex AIの利用
export GOOGLE_CLOUD_PROJECT="YOUR_PROJECT_ID"
```

---

## Gemini CLI - 基本的な使い方

### 起動

```bash
gemini
```

### 基本的なワークフロー

1. **タスクの説明**: 自然言語でやりたいことを説明
2. **コンテキストの提供**: 必要に応じて`@`を使用してファイルやディレクトリを指定
3. **実行と確認**: Gemini CLIがコードを生成・実行し、結果を確認

### 使用例

```bash
# コード生成
> Pythonでクイックソートを実装して

# エラーのデバッグ
> このエラーの原因と解決方法を教えて：TypeError: Cannot read property 'name' of undefined

# ファイル操作
> @src/app.js このコードを最適化し、パフォーマンスを改善してください

# Web検索
> 最新のPython 3.12の新機能について調べて、要約してください
```

### コマンド一覧

- `/memory`: テキストの内容をメモリに記憶させたり、記憶したメモリを表示・再読み込み
- `/compress`: 長く続いたチャットを要点だけにまとめ、トークン数の消費を抑える
- `/tools`: Gemini CLIに統合された外部ツールを一覧で確認

---

## Gemini CLI - コスト

### 無料枠

個人のGoogleアカウントでログインすることで、Gemini CLIは無料で利用可能です。

- **モデル**: Gemini 2.5 Pro
- **コンテキストウィンドウ**: 100万トークン
- **リクエスト数**: 
  - 毎分60回
  - 1日あたり1,000回

### 有料プラン

| モデル | 入力（100万トークンあたり） | 出力（100万トークンあたり） |
|--------|------------------------------|------------------------------|
| Gemini 2.5 Pro（20万トークン以下） | $1.25 | $10.00 |
| Gemini 2.5 Pro（20万トークン超） | $2.50 | $15.00 |
| Gemini 2.5 Flash | $0.30 | $2.50 |
| Gemini 2.0 Flash | $0.10 | $0.40 |

---

## Gemini CLI - 得意なこと・苦手なこと

### ✅ 得意なこと

- **コードの解析と生成**: 複雑なコードの解析や新規コードの生成が可能
- **タスクの自動化**: 繰り返し作業の自動化により、開発効率を向上
- **マルチモーダルデータの処理**: テキスト、画像、PDFなど多様な入力形式に対応
- **大規模なコードベースの理解**: 100万トークンのコンテキストウィンドウを活用し、複雑なリポジトリのアーキテクチャ把握が可能
- **Googleサービスとの連携**: Google検索機能を組み込み、最新のウェブ情報をリアルタイムで取得
- **開発ワークフローの自動化**: GitHubのプルリクエスト管理やコンフリクトの多いリベース作業の補助など、複数ステップのタスクを自動化

### ❌ 苦手なこと

- **複雑な処理や並列処理の課題**: 一部のユーザーから、複雑なタスクにおける応答速度の遅延や、エージェント能力の未熟さが指摘されている
- **オフライン環境での使用**: インターネット接続が必要で、オフラインでは利用できない
- **日本語対応の精度**: 一部の日本語生成において、不自然な表現が出力される場合がある
- **特定のドメイン知識が必要な高度な専門的タスク**: 専門的な知識を要するタスクでは、精度が落ちる可能性がある
- **パフォーマンスの不安定性**: プレビュー段階のため、パフォーマンスの不安定性が報告されている

---

## ⚡ Cursor CLI

<div style="text-align: center; margin-bottom: 15px;">
  <img src="assets/images/cursor-logo.svg" alt="Cursor Logo" style="width: 100px; height: 100px;">
</div>

### 概要

ターミナルから直接AIエージェントにアクセスし、コードの作成、レビュー、変更、ドキュメント化を行うための強力なコマンドラインツール

- **インタラクティブモード**: エージェントとの会話セッションを開始し、目標を伝えることができます
- **非対話モード（Printモード）**: スクリプト、CIパイプライン、自動化などの非対話シナリオに対応
- **セッション管理**: 以前の会話を再開し、複数回のやり取りにわたって文脈を維持
- **シェルモード**: 会話を離れずにCLIからシェルコマンドを直接実行可能
- **MCP（Model Context Protocol）サポート**: 拡張機能や統合のために使用可能
- **ルールシステム**: `.cursor/rules`ディレクトリにルールを作成して、エージェントにコンテキストとガイダンスを提供可能

---

## Cursor CLI - 主な特徴

### インタラクティブモード
- エージェントとの会話セッションを開始し、目標を伝えることができます
- 提案された変更を確認し、コマンドを承認できます
- 自然言語での指示に対応し、複雑なタスクを段階的に実行

### 非対話モード（Printモード）
- スクリプト、CIパイプライン、自動化などの非対話シナリオに対応
- 特定のプロンプトとモデルを指定して実行可能
- 出力形式を指定して結果を取得可能（テキスト形式など）
- 結果を標準出力に出力するため、CI/CDパイプラインへの統合が容易

### セッション管理
- 以前の会話を再開し、複数回のやり取りにわたって文脈を維持
- チャット履歴の一覧表示や特定の会話への復帰が可能
- 継続的な作業の文脈を保持し、長期的なタスクの管理に役立つ

---

## Cursor CLI - システム要件・インストール

### システム要件
- **OS**: macOS、Linux（Ubuntu 20.04+/Debian 10+など）、Windows（WSL2推奨）
- **シェル**: Bash、Zsh、またはFishで最適に動作
- **ネットワーク**: 認証とAI処理にインターネット接続が必要
- **アカウント**: Cursorアカウントが必要（無料プランまたは有料プラン）

### インストール方法（macOS）

```bash
# 公式インストールスクリプト（推奨）
curl https://cursor.com/install -fsS | bash

# または
curl -fsSL https://cursor.sh/install.sh | sh

# バージョン確認
cursor-agent --version

# PATHの設定（必要に応じて）
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### インストール後の設定

```bash
# 認証（初回実行時にCursorアカウントでログイン）
cursor-agent

# 動作確認
cursor-agent --version
cursor-agent --help
```

---

## Cursor CLI - 基本的な使い方

### 基本的なコマンド

```bash
# 対話セッションの開始
cursor-agent

# 初期プロンプトを指定して開始
cursor-agent "authモジュールをJWTトークンを用いるようにリファクタリングして"

# 非対話モードで実行
cursor-agent -p "パフォーマンス問題を見つけて修正して" --model "gpt-5"

# セッション一覧の表示
cursor-agent ls

# 直近の会話を再開
cursor-agent resume

# シェルモードでコマンドを実行
cursor-agent shell "ls -la"
```

### よく使うコマンド

```bash
# ヘルプの表示
cursor-agent --help

# バージョンの確認
cursor-agent --version

# 特定の会話を再開
cursor-agent --resume="chat-id-here"
```

---

## Cursor CLI - コスト

### 現在の料金プラン

Cursor CLIは現在**ベータ版**として提供されており、**無料で利用可能**です。

### Cursor IDEとの関係

Cursor CLIの利用料金は、Cursor IDEのプランに依存する可能性があります。

| プラン | 月額料金 | 備考 |
|--------|----------|------|
| 無料プラン | 無料 | 基本的な機能が利用可能（月間のリクエスト数に制限がある場合があります） |
| Proプラン | $20/月（年払い$17/月） | - |
| Businessプラン | $40/月（年払い） | - |
| Enterpriseプラン | 要問い合わせ | 2025年8月時点では、エンタープライズプランではCursor CLIが利用できない場合があります |

**注意**: 正式リリース後に料金プランが変更される可能性があります

---

## Cursor CLI - 得意なこと・苦手なこと

### ✅ 得意なこと

- **コード生成・修正・レビュー**: 自然言語での指示からコードを生成・修正。既存のコードに対するレビューや改善提案
- **コードリファクタリング**: コードの可読性や保守性を向上させるためのリファクタリングを支援
- **パフォーマンス最適化**: コードのパフォーマンス向上のための提案や修正
- **セキュリティレビュー**: コード内のセキュリティ上の問題点を検出し、脆弱性の修正案を提示
- **ドキュメント生成**: コードから自動的にドキュメントを生成
- **CI/CDパイプライン統合**: 非対話モードを活用して、CI/CDパイプライン内での自動化を実現
- **ターミナル統合**: IDEを開かずに、ターミナル内で直接AIによるコード生成やレビューが可能

### ❌ 苦手なこと

- **日本語対応の課題**: Cursor CLIは英語中心の設計であり、日本語でのコミットメッセージやドキュメント生成には課題があります
- **エンタープライズプランの制限**: 2025年8月時点では、エンタープライズプランが提供されておらず、大規模チームでの利用には制限があります
- **ベータ版の制限**: 現在ベータ版であるため、安定性や機能面での制限が存在する可能性があります
- **複雑なプロジェクトの全体的な理解**: 大規模で複雑なプロジェクト全体のコンテキストを完全に把握することは難しい場合があります
- **創造的な設計やアーキテクチャの提案**: 基本的な設計やアーキテクチャの提案は可能ですが、創造的で革新的な設計を求める場合、人間のエンジニアの判断が必要です

---

## 🐙 GitHub Copilot CLI

<div style="text-align: center; margin-bottom: 15px;">
  <img src="assets/images/github-copilot-logo.svg" alt="GitHub Copilot Logo" style="width: 100px; height: 100px;">
</div>

### 概要

GitHub CopilotのAIコーディング支援機能を直接ターミナル環境で利用できるコマンドラインインターフェース

- **ターミナルネイティブな開発**: ターミナル内で直接Copilotの機能を活用でき、作業の流れを中断することなくコーディングが可能
- **GitHubとの深い統合**: リポジトリ、Issue、プルリクエストなどのGitHubリソースに自然言語でアクセス可能
- **エージェント機能**: 複雑なタスクの計画や実行をAIが支援
- **MCPによる拡張性**: Model Context Protocol (MCP) サーバーを通じて機能拡張が可能
- **完全な制御と透明性**: すべてのアクションは実行前にプレビューされ、ユーザーの明示的な承認なしに何も実行されない

---

## GitHub Copilot CLI - 主な特徴

### GitHubとの深い統合
- リポジトリ、Issue、プルリクエストなどのGitHubリソースに自然言語でアクセス可能
- 既存のGitHubアカウントで認証が可能で、追加の設定が不要
- GitHubのワークフローとシームレスに連携
- GitHub MCPサーバーをデフォルトで使用し、GitHubリソースへのアクセスが容易

### エージェント機能
- 複雑なタスクの計画や実行をAIが支援
- コードの生成、編集、デバッグ、リファクタリングを自動でサポート
- タスクを適切に分解し、段階的に実行
- 高レベルな指示から詳細な実装まで自動で処理

### 完全な制御と透明性
- すべてのアクションは実行前にプレビューされる
- ユーザーの明示的な承認なしに何も実行されない
- ファイル変更やコマンド実行のすべてが可視化される
- 組織の既存のCopilotガバナンスポリシーを自動的に継承

---

## GitHub Copilot CLI - システム要件・インストール

### システム要件
- **OS**: macOS（完全サポート）、Linux（完全サポート）、Windows（WSL経由での利用が推奨、ネイティブサポートは実験的）
- **Node.js**: バージョン22以上（LTSバージョン推奨）
- **npm**: バージョン10以上
- **GitHub Copilotのサブスクリプション**: Copilot Pro、Copilot Pro+、Copilot Business、Copilot Enterprise
- **（Windowsの場合）**: PowerShell v6以上

### インストール方法（macOS）

```bash
# 方法1: Homebrewを使用する場合（推奨）
brew install node@22
npm install -g @github/copilot

# 方法2: npmを使用
npm install -g @github/copilot

# インストール確認
copilot --version

# 初回起動と認証
copilot
# 初回起動時には、GitHubアカウントでの認証が求められます
```

### Windowsでのインストール

```bash
# WSLを使用する場合（推奨）
# WSL内でLinuxと同様の手順でインストール

# ネイティブWindows環境（実験的）
npm install -g @github/copilot
```

---

## GitHub Copilot CLI - 基本的な使い方

### インタラクティブモード

```bash
# 対話型セッションが開始され、自然言語で質問やタスクの指示が可能
copilot
```

### プログラムモード

```bash
# コマンドラインで直接プロンプトを渡す
copilot -p "List my open PRs" --allow-all-tools
```

### スラッシュコマンド

- **`/model`**: 利用可能なAIモデルを選択・変更
  - デフォルト: Claude Sonnet 4.5
  - 利用可能: GPT-5、Gemini 2.5 Pro（プレミアムプラン）など
- **`/feedback`**: フィードバックの送信
- **`/login`**: 再認証の実行（必要に応じて）

### 特殊なコマンド構文

```bash
# 一般的なシェルコマンドの生成や説明
?? how to find files modified in last 7 days

# Gitコマンドに特化した支援
git? how to undo the last commit

# GitHub CLIコマンドの生成や説明
gh? how to create a new repository
```

### ファイル参照

```bash
# プロンプト内で@記号を使用して特定のファイルを参照
@src/components/Button.tsx このコンポーネントをリファクタリングしてください
```

---

## GitHub Copilot CLI - コスト

### サブスクリプションプラン

GitHub Copilot CLIは、GitHub Copilotの有料サブスクリプションプランに含まれています。追加の料金やAPIキーは不要です。

| プラン | 月額料金 | 対象 | GitHub Copilot CLI |
|--------|----------|------|-------------------|
| **Copilot Pro** | $10/月（年払い$100） | 個人開発者 | ✅ 含まれる |
| **Copilot Pro+** | $39/月（年払い$390） | 個人開発者向けの上位プラン | ✅ 含まれる |
| **Copilot Business** | $19/ユーザー/月 | チームや組織 | ✅ 含まれる |
| **Copilot Enterprise** | $39/ユーザー/月 | 大規模組織 | ✅ 含まれる |

### プレミアムリクエストの仕組み

- **消費単位**: Copilot CLIへの各プロンプト送信ごとに、**1つのプレミアムリクエストが消費**されます
- **クォータ**: プランごとに月次のプレミアムリクエスト許容量が設定されています
- **確認方法**: 対話型セッション内でクォータの残りを確認できます

---

## GitHub Copilot CLI - 得意なこと・苦手なこと

### ✅ 得意なこと

- **コードベースのメンテナンス**: セキュリティ関連の修正、依存関係のアップグレード、リファクタリング作業、コードクリーンアップ
- **ドキュメント作成**: コードのドキュメント生成、既存ドキュメントの更新、APIドキュメントの作成、READMEファイルの作成・更新
- **機能開発**: 新機能のプロトタイプ作成、機能要求の段階的な実装、小規模から中規模の機能追加
- **テストカバレッジの向上**: 追加テストスイートの開発、ユニットテストの作成、統合テストの作成、エッジケースのテスト追加
- **環境のセットアップ**: ローカル環境の設定、依存関係のインストール、設定ファイルの作成、開発環境の構築
- **コマンドの提案と説明**: 適切なコマンドの提案、コマンドの機能と目的の説明、複雑なコマンドの組み合わせ
- **GitHubリソースとの連携**: Issueやプルリクエストの操作、リポジトリ情報の取得、GitHubワークフローの自動化

### ❌ 苦手なこと

- **複雑なタスクの完全自動化**: 複雑で抽象的な指示に対する正確な応答が難しい場合がある
- **最新技術への対応**: 最新のライブラリやフレームワークに関する情報が不足している場合がある
- **セキュリティ上の懸念**: 生成されたコードが常に安全であるとは限らない。常にレビューと検証が必要
- **大規模プロジェクトの理解**: 大規模で複雑なプロジェクト全体の文脈を完全に理解するのは難しい
- **GUI操作**: ターミナルベースのため、GUI操作が必要なタスクには適していない
- **高度なカスタマイズ**: 特定の開発環境やワークフローに強く依存する場合、適切な提案が得られないことがある

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

## 📊 ツール比較表 - 基本情報

| ツール名 | 開発元 | ライセンス | 主要モデル | 対応OS |
|---------|--------|-----------|-----------|--------|
| **Claude Code** | Anthropic | プロプライエタリ | Claude Sonnet 4.5 / Opus 4.1 | macOS, Linux, Windows(WSL) |
| **Codex CLI** | OpenAI | オープンソース | GPT-4o, o3, o4-mini, codex-mini | macOS, Linux, Windows(WSL) |
| **Gemini CLI** | Google | オープンソース | Gemini 2.5 Pro / Flash | macOS, Linux, Windows(WSL) |
| **Cursor CLI** | Cursor | プロプライエタリ | GPT-5, Claude Sonnet 4.5 | macOS, Linux, Windows(WSL) |
| **GitHub Copilot CLI** | GitHub | プロプライエタリ | Claude Sonnet 4.5 (デフォルト) | macOS, Linux, Windows(WSL) |

---

## 📊 ツール比較表 - コスト

| ツール名 | 料金プラン | 最低料金 | 特徴 |
|---------|-----------|---------|------|
| **Claude Code** | Pro / Max / Team / Enterprise | $20/月 | 使用量制限あり（45回/5時間〜） |
| **Codex CLI** | ChatGPT Plus / Pro / Team / Enterprise | $20/月 | CLI自体は無料、API利用料が発生 |
| **Gemini CLI** | 無料枠 / 従量課金 | 無料 | 無料枠あり（毎分60回、1日1,000回） |
| **Cursor CLI** | 無料（ベータ版） / Pro / Business | 無料 | ベータ版は無料、正式リリース後は未定 |
| **GitHub Copilot CLI** | Copilot Pro / Pro+ / Business / Enterprise | $10/月 | Copilotサブスクリプションに含まれる |

---

## 📊 ツール比較表 - 機能比較

| 機能 | Claude Code | Codex CLI | Gemini CLI | Cursor CLI | GitHub Copilot CLI |
|------|------------|-----------|------------|------------|-------------------|
| **コード生成** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **コードレビュー** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **リファクタリング** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **テスト生成** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **GitHub統合** | ✅ | ❌ | ❌ | ❌ | ✅✅ |
| **MCPサポート** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **サンドボックス** | ❌ | ✅ | ✅ | ❌ | ❌ |
| **マルチモーダル** | ❌ | ✅ | ✅ | ✅ | ❌ |
| **Web検索** | ❌ | ❌ | ✅ | ❌ | ❌ |
| **セッション管理** | ✅ | ❌ | ✅ | ✅ | ❌ |

---

## 📊 ツール比較表 - 得意分野

| ツール名 | 特に得意なこと | 特徴的な機能 |
|---------|--------------|------------|
| **Claude Code** | CI/CD支援、コードレビュー、GitHub統合 | Planモード、サブエージェント、カスタムスラッシュコマンド |
| **Codex CLI** | ローカル実行、プライバシー保護、サンドボックス | `--full-auto`モード、AGENTS.mdカスタマイズ |
| **Gemini CLI** | 大規模コードベース、マルチモーダル、Web検索 | 100万トークンコンテキスト、Google検索統合 |
| **Cursor CLI** | IDE統合、CI/CD統合、セッション管理 | Printモード、シェルモード、ルールシステム |
| **GitHub Copilot CLI** | GitHubワークフロー、コードメンテナンス | GitHub MCPサーバー、完全な制御と透明性 |

---

## 📊 ツール比較表 - 苦手なこと

| ツール名 | 主な制限・苦手なこと |
|---------|-------------------|
| **Claude Code** | 大規模コードベース、セキュリティコード、創造的設計 |
| **Codex CLI** | 複雑なプロジェクト理解、多ステップ大規模変更、最新技術対応 |
| **Gemini CLI** | 複雑な並列処理、日本語精度、パフォーマンス不安定性 |
| **Cursor CLI** | 日本語対応、エンタープライズ制限、ベータ版の制限 |
| **GitHub Copilot CLI** | 複雑なタスク自動化、最新技術対応、GUI操作 |

---

## 🎯 選択のポイント

### 用途別のおすすめ

#### GitHub中心の開発
- **GitHub Copilot CLI**: GitHubとの統合が最も強力
- **Claude Code**: GitHub Actions連携、CI/CD支援が得意

#### プライバシー重視
- **Codex CLI**: ローカル実行、サンドボックスモードで安全性が高い
- **Gemini CLI**: 無料枠で試せる

#### 大規模プロジェクト
- **Gemini CLI**: 100万トークンのコンテキストウィンドウが強力
- **Claude Code**: Maxプランで大規模コードベースに対応

#### CI/CD統合
- **Cursor CLI**: PrintモードでCI/CDパイプラインに統合しやすい
- **GitHub Copilot CLI**: GitHub Actionsとの統合が容易

#### コスト重視
- **Gemini CLI**: 無料枠が充実
- **Cursor CLI**: ベータ版は無料

---

## まとめ

### 主要ツールの特徴まとめ

- **Claude Code**: AnthropicのClaudeモデルを使用。エージェント型コーディング、GitHub統合、Planモードなど高度な機能が充実
- **Codex CLI**: OpenAIのオープンソースツール。ローカル実行重視、プライバシー保護、サンドボックス機能が強み
- **Gemini CLI**: Googleのオープンソースツール。100万トークンコンテキスト、マルチモーダル、Web検索統合が特徴
- **Cursor CLI**: Cursor IDEと統合。Printモード、セッション管理、CI/CD統合が得意
- **GitHub Copilot CLI**: GitHubとの統合が最も強力。GitHubワークフローに最適化、完全な制御と透明性

### 選択のポイント

1. **プロジェクトの要件**: GitHub中心ならGitHub Copilot CLI、プライバシー重視ならCodex CLI
2. **コスト**: 無料枠ならGemini CLI、既存のサブスクリプションを活用
3. **機能要件**: 大規模コードベースならGemini CLI、CI/CD統合ならCursor CLI
4. **開発環境**: IDE統合ならCursor CLI、ターミナル中心ならCodex CLI

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

