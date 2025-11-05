# Gemini CLI

## 概要・特徴

Gemini CLIは、Googleが2025年6月に発表したオープンソースのAIエージェントツールで、ターミナルから直接AIモデル「Gemini」を利用できるコマンドラインインターフェースです。開発者はこれを使用して、コード生成、ファイル管理、ツールの呼び出し、他のアプリとの連携、コンテキストの理解など、多岐にわたるタスクを効率的に実行できます。

### 主な特徴

- **大規模コンテキスト処理**: 最大100万トークンのコンテキストウィンドウを持ち、複雑なコードベースの理解や編集が可能
- **マルチモーダル対応**: テキストだけでなく、画像やPDFなどの多様な入力形式を処理
- **ReActループの採用**: 「思考→ツール実行→回答生成」というステップを繰り返し、複雑なタスクを効率的に処理
- **Google検索との統合**: リアルタイムでウェブから情報を取得し、外部コンテキストをモデルに提供
- **MCP（Model Context Protocol）対応**: 外部ツールとの柔軟な連携が可能
- **オープンソース**: 完全オープンソースで提供され、カスタマイズや拡張が容易

## コスト

### 無料枠

個人のGoogleアカウントでログインすることで、Gemini CLIは無料で利用可能です。無料ライセンスでは以下の利用枠が提供されます：

- **モデル**: Gemini 2.5 Pro
- **コンテキストウィンドウ**: 100万トークン
- **リクエスト数**: 
  - 毎分60回
  - 1日あたり1,000回

### 有料プラン

より多くのリクエストや特定のモデルを優先的に利用したい場合は、以下のオプションがあります：

#### Google AI Studio / Vertex AI の従量課金

| モデル | 入力（100万トークンあたり） | 出力（100万トークンあたり） |
|--------|------------------------------|------------------------------|
| Gemini 2.5 Pro（20万トークン以下） | $1.25 | $10.00 |
| Gemini 2.5 Pro（20万トークン超） | $2.50 | $15.00 |
| Gemini 2.5 Flash | $0.30 | $2.50 |
| Gemini 2.0 Flash | $0.10 | $0.40 |

#### Gemini Code Assist ライセンス

- **Standard版**: 有料ライセンス（詳細は公式に問い合わせ）
- **Enterprise版**: エンタープライズ向け有料ライセンス（詳細は公式に問い合わせ）

## インストール方法

### 前提条件

- **Node.js**: バージョン18以上が必要
- **OS**: macOS、Linux、Windows（WSL経由）に対応

### macOS

#### 方法1: npmを使用（推奨）

1. **Node.jsのインストール確認**
   ```bash
   node --version
   ```
   Node.js v18以上がインストールされていることを確認してください。

2. **Homebrewを使用してNode.jsをインストール（未インストールの場合）**
   ```bash
   brew install node
   ```

3. **Gemini CLIのインストール**
   ```bash
   npm install -g @google/gemini-cli
   ```

4. **インストールの確認**
   ```bash
   gemini --version
   ```
   バージョン情報が表示されれば、インストールは成功です。

#### 方法2: npxを使用（一時的な実行）

インストールせずに試用したい場合は、以下のコマンドを使用します：

```bash
npx @google/gemini-cli
```

### Windows

#### 方法1: npmを使用（推奨）

1. **Node.jsのインストール**
   - [Node.js公式サイト](https://nodejs.org/)からLTS版をダウンロード
   - インストーラーを実行してインストール

2. **Gemini CLIのインストール**
   コマンドプロンプトまたはPowerShellを開き、以下のコマンドを実行します：
   ```bash
   npm install -g @google/gemini-cli
   ```

3. **インストールの確認**
   ```bash
   gemini --version
   ```
   バージョン情報が表示されれば、インストールは成功です。

#### 方法2: WSL（Windows Subsystem for Linux）を使用

Windows上でLinux環境を使用する場合：

1. WSLをインストール（未インストールの場合）
2. Linuxディストリビューションをインストール
3. Linuxターミナルで以下のコマンドを実行：
   ```bash
   npm install -g @google/gemini-cli
   ```

### 認証方法

初回起動時に認証が必要です。以下の方法から選択できます：

#### 1. Googleアカウントでの認証（推奨・無料枠利用）

1. `gemini`コマンドを実行
2. テーマカラーを選択
3. ブラウザが自動で起動するので、Googleアカウントでログイン
4. 認証コードをターミナルに入力して認証を完了

これにより、無料枠が利用可能になります。

#### 2. APIキーの使用

Google AI Studioで取得したAPIキーを使用する場合：

```bash
export GEMINI_API_KEY="YOUR_API_KEY"
```

または、Windowsの場合：

```cmd
set GEMINI_API_KEY=YOUR_API_KEY
```

#### 3. Vertex AIの利用

Google Cloudプロジェクトと連携する場合：

```bash
export GOOGLE_CLOUD_PROJECT="YOUR_PROJECT_ID"
```

## 特徴や得意なこと・苦手なこと

### 特徴

- **大規模コードベースのサポート**: 100万トークン以上のコンテキストを処理でき、大規模なプロジェクトの分析が容易
- **マルチモーダルアプリのプロトタイピング**: PDFやスケッチからアプリのプロトタイプを迅速に生成
- **DevOpsタスクの自動化**: Git操作、プルリクエストの取得、移行計画の作成などが可能
- **ツール統合**: MCPサーバーを介して、Imagen、Veo、Lyriaなどのメディア生成モデルに接続
- **ウェブ検索対応**: 組み込みのGoogle検索により、最新で信頼性の高い回答が得られる
- **高い導入の容易さ**: npmで簡単にインストールでき、Windowsネイティブ対応しているため、導入ハードルが低い

### 得意なこと

- **コードの解析と生成**: 複雑なコードの解析や新規コードの生成が可能
- **タスクの自動化**: 繰り返し作業の自動化により、開発効率を向上
- **マルチモーダルデータの処理**: テキスト、画像、PDFなど多様な入力形式に対応
- **大規模なコードベースの理解**: 100万トークンのコンテキストウィンドウを活用し、複雑なリポジトリのアーキテクチャ把握が可能
- **Googleサービスとの連携**: Google検索機能を組み込み、最新のウェブ情報をリアルタイムで取得
- **開発ワークフローの自動化**: GitHubのプルリクエスト管理やコンフリクトの多いリベース作業の補助など、複数ステップのタスクを自動化

### 苦手なこと

- **複雑な処理や並列処理の課題**: 一部のユーザーから、複雑なタスクにおける応答速度の遅延や、エージェント能力の未熟さが指摘されている
- **オフライン環境での使用**: インターネット接続が必要で、オフラインでは利用できない
- **日本語対応の精度**: 一部の日本語生成において、不自然な表現が出力される場合がある
- **特定のドメイン知識が必要な高度な専門的タスク**: 専門的な知識を要するタスクでは、精度が落ちる可能性がある
- **リアルタイムでの大量データ処理**: リアルタイムでの大量データ処理には限界がある
- **パフォーマンスの不安定性**: プレビュー段階のため、パフォーマンスの不安定性が報告されている
- **コード品質の一貫性**: コード品質の一貫性に課題があると指摘されている

## 実装されている機能

### 基本機能

- **コード生成・レビュー・実行支援**: 自然言語での指示に基づき、コードの生成やレビュー、実行をサポート
- **ファイル操作**: ファイルの作成、編集、整理などの操作をAIに指示可能
  - `ReadFile`: ファイル内容の読み込み
  - `Edit`: ファイルの編集と差分表示
  - `SearchText`: プロジェクト全体での文字列検索
- **システム操作**: シェルコマンドの安全な実行
  - `Shell`: シェルコマンドの実行
  - Dockerサンドボックス: 隔離された実行環境の提供

### 統合機能

- **Google検索との連携**: プロンプトの根拠付けとしてウェブページを取得し、リアルタイムの外部コンテキストをモデルに提供
- **Web検索機能**: ターミナル上でWeb情報の取得と要約が可能
  - `GoogleSearch`: Google検索結果の取得
  - `WebFetch`: Webページのコンテンツ取得

### 拡張機能

- **MCPサーバーのサポート**: Model Context Protocol（MCP）の組み込みサポートやバンドルされた拡張機能を通じて、Gemini CLIの機能を拡張可能
  - カスタムツールの追加
  - 外部ツールとの連携（Jira、社内DBなど）
  - Imagen、Veo、Lyriaなどのメディア生成モデルへの接続
- **プロジェクト特化型アシスタント**: プロジェクトごとのルールや文脈を学習させ、専用アシスタントとして動作可能
  - `GEMINI.md`ファイルによるプロジェクト固有の指示設定
- **プロンプトと指示のカスタマイズ**: 特定のニーズやワークフローに合わせてGeminiを調整可能

### コマンド一覧

#### 対話コマンド

- `/memory`: テキストの内容をメモリに記憶させたり、記憶したメモリを表示・再読み込み
- `/compress`: 長く続いたチャットを要点だけにまとめ、トークン数の消費を抑える
- `/tools`: Gemini CLIに統合された外部ツールを一覧で確認

#### ファイル参照

- `@ファイル名`: ファイルの内容をGeminiへの入力に組み込む
- `@ディレクトリ名`: ディレクトリ全体の内容をGeminiへの入力に組み込む

### 自動化機能

- **スクリプト内での非対話的呼び出し**: タスクを自動化し、既存のワークフローと統合可能
- **CI/CDパイプラインへの統合**: シェルスクリプトから非対話的に呼び出し、CI/CDパイプラインやシェルスクリプトに組み込むことが可能

### その他の機能

- **コード解析と修正**: ローカルファイルのバグ検出や修正提案を自然言語で実行
- **外部ツールとの連携**: データベースやデザインプラットフォーム、決済サービスなど、多様なツールと統合可能
- **拡張機能のサポート**: オープンエコシステムを採用し、誰でも拡張機能を構築・共有可能

## 基本的な使い方

### 起動

```bash
gemini
```

### 基本的なワークフロー

1. **タスクの説明**: 自然言語でやりたいことを説明
2. **コンテキストの提供**: 必要に応じて`@`を使用してファイルやディレクトリを指定
3. **実行と確認**: Gemini CLIがコードを生成・実行し、結果を確認

### 使用例

#### コード生成
```
> Pythonでクイックソートを実装して
```

#### エラーのデバッグ
```
> このエラーの原因と解決方法を教えて：TypeError: Cannot read property 'name' of undefined
```

#### ファイル操作
```
> @src/app.js このコードを最適化し、パフォーマンスを改善してください
```

#### Web検索
```
> 最新のPython 3.12の新機能について調べて、要約してください
```

## 使用例・デモ

### 例1: コード生成と最適化

```bash
gemini
> @src/main.py このコードを最適化して、バグを修正してください
```

Gemini CLIは以下を自動的に実行します：
- コードの分析
- バグの特定
- 最適化の提案と実装
- 変更内容の差分を表示

### 例2: プロジェクト構造の理解

```bash
gemini
> @src/ このプロジェクトの構造を説明し、処理フローを図解付きで解説してください
```

### 例3: DevOpsタスクの自動化

```bash
gemini
> GitHubのプルリクエストを取得して、変更内容を要約してください
```

### 例4: マルチモーダル処理

```bash
gemini
> @design.pdf この仕様書からアプリケーションのプロトタイプを生成してください
```

### 例5: プロジェクト特化型アシスタントの設定

プロジェクトのルートディレクトリに`GEMINI.md`ファイルを作成：

```markdown
# プロジェクト設定

このプロジェクトはTypeScriptで書かれたReactアプリケーションです。
- ESLintとPrettierを使用しています
- コンポーネントは関数型コンポーネントのみを使用します
- テストはJestとReact Testing Libraryを使用します
```

## 参考資料

### 公式ドキュメント

- [Gemini CLI : オープンソース AI エージェント | Google Cloud 公式ブログ](https://cloud.google.com/blog/ja/topics/developers-practitioners/introducing-gemini-cli)
- [Gemini CLI GitHub Repository](https://github.com/google/gemini-cli)
- [Gemini CLI Extensions for Google Data Cloud | Google Cloud Blog](https://cloud.google.com/blog/ja/products/databases/gemini-cli-extensions-for-google-data-cloud)
- [Automate App Deployment and Security Analysis with New Gemini CLI Extensions | Google Cloud Blog](https://cloud.google.com/blog/ja/products/ai-machine-learning/automate-app-deployment-and-security-analysis-with-new-gemini-cli-extensions)

### NPMパッケージ

- [@google/gemini-cli](https://www.npmjs.com/package/@google/gemini-cli)

### 日本語記事・ガイド

- [Gemini CLI完全ガイド：2025年版コマンドラインAIアシスタントの使い方と活用法 | Zenn](https://zenn.dev/yusuke8901/articles/gemini-cli-complete-guide)
- [Gemini CLI のインストール方法と基本的な使い方 | Zenn](https://zenn.dev/torakm/articles/b844f29c9d349c)
- [Gemini CLI完全ガイド：Googleの革新的AIコマンドラインツールを徹底解説 | Zenn](https://zenn.dev/takuh/articles/fc18f26f7a24f6)
- [初心者でも分かる！VSCodeでGemini CLIを使いこなす方法 - インストールから応用まで徹底解説 | Qiita](https://qiita.com/Nakamura-Kaito/items/122963855d7b1deb8a9d)
- [Gemini CLIとは？インストール方法から使い方、料金プランを解説 | 株式会社ProFab](https://profab.co.jp/what-is-gemini-cli/)
- [Gemini CLIとは？使い方と料金！無料でターミナルから直接AIを動かせる | MiraLabAI](https://miralab.co.jp/media/gemini_cli/)
- [Gemini CLI使い方完全ガイド｜インストールから実践まで初心者向け徹底解説 | テックジム](https://techgym.jp/column/gemini-cli/)
- [Gemini CLI のプロンプト設計術：高精度応答を引き出すテクニック 20 選 | T-CREATOR](https://t-cr.jp/article/v861j474npccwug)
- [Gemini CLI完全ガイド：初心者でも3ステップで作業自動化を実現する方法 | キレカク](https://kirekaku.com/1739/)
- [Gemini CLIとは？Google の最新AIエージェントの特徴や使い方・料金・活用例を詳しく解説 | AISmiley](https://aismiley.co.jp/ai_news/gemini-cli-google-code-assist-use/)
- [2025年の決定版：Google Gemini CLI完全ガイド - ターミナルにAIを統合する新時代の開発ツール | walk-with-ai](https://www.walk-with-ai.com/blog/google-gemini-cli-comprehensive-guide)
- [Gemini CLIでできることとは？インストール方法や使い方を徹底解説 | Stella International](https://stella-international.co.jp/ai/gemini-cli-how-to-use/)
- [Gemini CLI徹底解説：ターミナルでAIを活用する究極ガイド | Qiita](https://qiita.com/TechTW/items/187cd341f202f8291dc9)
- [Gemini CLI エクステンション：AI搭載コマンドラインカスタマイゼーションの完全開発者ガイド（2025年版） | Qiita](https://qiita.com/sienna1988/items/5ada90946f3a4a0ff6e2)
- [Gemini CLIリリース直後の評価まとめ | Zenn](https://zenn.dev/serada/articles/20250626-gemini-cli-review)
- [Gemini CLIとは？Google発AIエージェントの使い方やインストール方法を徹底解説 | WEEL](https://weel.co.jp/media/tech/gemini-cli/)
- [Gemini CLI使い方完全ガイド！インストールから効率的な自動化まで徹底解説 | ライティングコラム](https://writing-corp.co.jp/media/gemini-cli/)
- [Gemini CLI vs Claude Code 徹底比較 | Taskhub](https://taskhub.jp/useful/gemini-cli-claude-code/)
- [Gemini CLIを徹底解説：インストールから実践まで | 株式会社dotConf](https://note.com/dotconf/n/n2da5f402c0e6)
- [Gemini CLIの使い方完全ガイド！インストールから実践ユースケースまで | Taskhub](https://taskhub.jp/useful/gemini-cli-usage/)
- [gemini cli とは？初心者向けに機能・使い方・料金・安全性を完全解説 | Gemini Guide](https://www.geminiguide.jp/gemini-cli-guide-3/)
- [Gemini CLIの導入 | Zenn](https://zenn.dev/fried_shrimp/scraps/5f4b99fd7ef10b)
- [「Gemini CLI」基礎編、インストール方法から使い方まで徹底解説 | Lilys.ai](https://lilys.ai/notes/ja/gemini-cli-20251021/gemini-cli-basics-install-usage-guide)
- [Gemini CLIのシステムプロンプトを初心者向けに徹底解説！ | Zenn](https://zenn.dev/daideguchi/articles/3258ec6b8e4c00)
- [Gemini CLIの簡単インストール方法 | Lynx SEO](https://lynx-seo.co.jp/blog/gemini-cli-install/)
- [Gemini CLIとは何か？ | 株式会社一創](https://www.issoh.co.jp/tech/details/7470/)
- [Gemini CLI 入門 | T-CREATOR](https://t-cr.jp/article/0241j3qagrful3c)
- [話題のAIツール「Gemini CLI」とは？ | EdgeHUB](https://highreso.jp/edgehub/wordgenerationai/gemini-cli.html)
- [Gemini CLIの使い方を解説！インストール・基本コマンド・エラー解決まで | AI経営総合研究所](https://ai-keiei.shift-ai.co.jp/gemini-cli-usage/)
- [Gemini CLIの使い方 | 窓の杜](https://forest.watch.impress.co.jp/docs/serial/yaaiwatch/2031780.html)

### セキュリティ関連

- [Google Gemini Security Flaw | TechRadar](https://www.techradar.com/pro/security/google-gemini-security-flaw-could-have-let-anyone-access-systems-or-run-code)
- [Gemini CLI Security Flaw | IT Pro](https://www.itpro.com/security/a-flaw-in-googles-new-gemini-cli-tool-couldve-allowed-hackers-to-exfiltrate-data)

### ニュース・発表

- [Google Gemini and GitHub Partnership | TechRadar](https://www.techradar.com/pro/google-gemini-and-github-are-teaming-up-for-ai-powered-coding)
- [Gemini CLI and Zed Code Editor Partnership | Android Central](https://www.androidcentral.com/apps-software/ai/gemini-cli-zed-code-editor-partnership)
