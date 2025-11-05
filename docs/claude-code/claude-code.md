# Claude Code

## 概要・特徴

Claude Codeは、Anthropic社が開発したエージェント型のAIコーディング支援ツールです。ターミナル上で動作し、自然言語による指示でコードの生成、編集、デバッグ、リファクタリングなどを自律的に行うことができます。

### 主な特徴

- **エージェント型コーディング**: 自然言語での指示に基づき、コードの生成、修正、リファクタリング、テスト実行などを自律的に実行します
- **多言語対応**: JavaScript/TypeScript、Python、Java、C++、Go、Rust、PHP、Ruby、HTML/CSS、SQL、シェルスクリプトなど、主要なプログラミング言語に対応
- **GitHub統合**: GitHub Actionsと連携し、CI/CDパイプラインの自動化をサポート。プルリクエストの自動修正やテストの追加、ドキュメント生成などが可能
- **プロジェクト全体の理解**: プロジェクト全体を読み込み、構成や機能を解析し、適切なコード生成や編集を行います
- **対話型インターフェース**: ターミナル上での自然言語による対話を通じて、段階的に作業を進めることができます

## コスト

Claude Codeの利用には、以下の料金プランが用意されています。

### サブスクリプションプラン

#### Proプラン
- **料金**: 月額$20（年間契約の場合は月額$17）
- **モデル**: Sonnet 4.5を使用
- **用途**: 小規模なコードベースでの短期間のコーディングに適しています
- **制限**: 約45回/5時間の使用制限があります。初心者には十分ですが、本格的に使用すると上限に達する可能性があります

#### Maxプラン
- **料金**: 月額$100（Max 5xプラン）または月額$200（Max 20xプラン）
- **モデル**: Sonnet 4.5とOpus 4.1の両方にアクセス可能
- **用途**: 大規模なコードベースでの日常的な使用に適しています
- **制限**: 
  - Max 5xプラン: 約225回/5時間（Proプランの5倍）
  - Max 20xプラン: 約900回/5時間（Proプランの20倍）

#### Teamプラン
- **料金**: 1ユーザーあたり月額$150（最低5人のメンバーが必要）
- **モデル**: Sonnet 4.5とOpus 4.1の両方にアクセス可能
- **機能**: 
  - セルフサービスのシート管理
  - 標準API料金での追加使用量
  - チーム管理機能

#### Enterpriseプラン
- **料金**: 営業担当者にお問い合わせください
- **機能**: Teamプランの全機能に加え、以下が含まれます：
  - 高度なセキュリティ
  - データ管理
  - ユーザー管理
  - 専用サポート

### API従量課金プラン

使用したトークン量に応じて料金が発生します。モデルごとの料金は以下の通りです：

- **Claude 3 Opus**: 入力1Mトークンあたり$15、出力1Mトークンあたり$75
- **Claude 3 Sonnet**: 入力1Mトークンあたり$3、出力1Mトークンあたり$15
- **Claude 3 Haiku**: 入力1Mトークンあたり$0.25、出力1Mトークンあたり$1.25

### コスト管理

- **平均的なコスト**: 開発者1人あたり1日約$6程度。ユーザーの90%は1日$12未満で利用しています
- **使用量の確認**: `/cost`コマンドで現在のセッションの使用量を確認できます
- **コスト削減の方法**:
  - 不要な会話履歴の削除
  - 会話のコンパクト化
  - 大きなタスクの分割
  - Anthropic Consoleで履歴使用量を確認

## インストール方法

### システム要件

- **オペレーティングシステム**: 
  - macOS 10.15以降
  - Ubuntu 20.04+/Debian 10+
  - Windows 10+（WSL 1、WSL 2、またはGit for Windowsを使用。ネイティブ動作も可能）
- **ハードウェア**: 4GB以上のRAM
- **ソフトウェア**: Node.js 18以上、npmまたはyarn
- **ネットワーク**: 認証とAI処理にインターネット接続が必要（オフライン使用不可）
- **シェル**: Bash、Zsh、またはFishで最適に動作
- **アカウント**: ProまたはMaxプランのサブスクリプションが必要

### macOS

1. **Node.jsとnpmの確認**
   ```bash
   node --version
   npm --version
   ```
   Node.js 18以上がインストールされていることを確認してください。インストールされていない場合は、[Node.js公式サイト](https://nodejs.org/)から最新のLTSバージョンをダウンロードしてインストールします。

2. **Claude Codeのインストール**
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```
   
   **重要**: `sudo npm install -g`は使用しないでください。権限の問題やセキュリティリスクを引き起こす可能性があります。権限エラーが発生した場合は、公式ドキュメントの推奨解決策を参照してください。

3. **バージョン確認**
   ```bash
   claude --version
   ```
   インストールが成功したことを確認します。

4. **認証**
   ```bash
   claude login
   ```
   または単に：
   ```bash
   claude
   ```
   プロンプトに従ってログイン方法を選択します。ブラウザで認証画面が表示されるので、Anthropicアカウントでサインインして許可を行います。

5. **プロジェクトの初期化（オプション）**
   ```bash
   claude init
   ```
   プロジェクトディレクトリで実行すると、設定ファイルとメモリを生成します。

### Windows

#### 方法1: ネイティブインストール（推奨）

1. **Node.jsとnpmの確認**
   PowerShellまたはコマンドプロンプトを開き、以下のコマンドを実行します：
   ```powershell
   node --version
   npm --version
   ```
   Node.js 18以上がインストールされていることを確認してください。インストールされていない場合は、[Node.js公式サイト](https://nodejs.org/)から最新のLTSバージョンをダウンロードしてインストールします。

2. **Claude Codeのインストール**
   管理者権限でPowerShellを開き、以下のコマンドを実行します：
   ```powershell
   npm install -g @anthropic-ai/claude-code
   ```

3. **バージョン確認**
   ```powershell
   claude --version
   ```
   インストールが成功したことを確認します。

4. **認証**
   ```powershell
   claude login
   ```
   または：
   ```powershell
   claude
   ```
   プロンプトに従ってログイン方法を選択します。ブラウザで認証画面が表示されるので、Anthropicアカウントでサインインして許可を行います。

#### 方法2: WSL経由でのインストール

Windows Subsystem for Linux（WSL）を使用する場合：

1. **WSLのセットアップ**
   WSL 1またはWSL 2をインストールし、UbuntuまたはDebianディストリビューションをセットアップします。

2. **WSL内でmacOSと同じ手順を実行**
   WSLターミナルを開き、macOSの手順と同じようにNode.jsとClaude Codeをインストールします。

### トラブルシューティング

- **権限エラー**: `sudo npm install -g`の使用は推奨されていません。代わりに、npmのグローバルインストールパスを変更するか、nvmを使用してください
- **インストールエラー**: Node.jsのバージョンが18以上であることを確認してください
- **認証エラー**: ブラウザで認証が完了しているか確認し、APIキーが正しく設定されているか確認してください

## 特徴や得意なこと・苦手なこと

### 特徴

- **エージェント型コーディング**: 自然言語での指示に基づき、コードの生成、修正、リファクタリング、テスト実行などを自律的に実行します
- **多言語対応**: 日本語を含む複数の言語での対話が可能で、複数のプログラミング言語に対応しています
- **GitHub統合**: GitHub Actionsと連携し、CI/CDパイプラインの自動化をサポートします
- **プロジェクト全体の理解**: プロジェクト全体を読み込み、構成や機能を解析し、適切なコード生成や編集を行います
- **対話型インターフェース**: ターミナル上での自然言語による対話を通じて、段階的に作業を進めることができます
- **VS Code拡張機能**: GUIベースのIDEでもClaude Codeを活用できます

### 得意なこと

- **コードの自動生成と編集**: 要件を伝えるだけで、適切なコード構造やアーキテクチャを提案し、コードを生成・修正します
- **コードレビュー**: コミット差分を解析し、自動でレビューコメントや改善提案を生成します
- **CI/CD支援**: DockerfileやGitHub ActionsのYAMLを自動生成し、効率的な開発フローを実現します
- **リファクタリング**: コードの品質向上のためのリファクタリング提案を行い、自動で実行することも可能です
- **テスト生成**: コードに対するテストケースを自動生成し、品質向上をサポートします
- **デバッグ支援**: エラーメッセージの解析やバグの特定を支援し、修正案を提示します
- **プロジェクトの理解と説明**: プロジェクト全体を解析し、構成や機能を説明することができます
- **複雑なタスクの自動化**: 複数のステップからなるタスクを自律的に計画・実行します

### 苦手なこと

- **大規模で複雑なコードベースの処理**: 大規模で複雑なコードベースでは、AIの性能が制限される場合があります。プロジェクト全体の文脈を完全に理解するのは難しい場合があります
- **プロジェクト固有の暗黙知の活用**: 文書化されていないプロジェクト固有の知識をAIが活用することは困難です
- **セキュリティ関連のコード**: 認証・認可周りのコードは、必ず人間がレビューする必要があります。プロンプトインジェクションへの脆弱性もあるため、重要な操作の際はユーザーの確認が必要です
- **パフォーマンスクリティカルな処理**: N+1クエリやメモリリークを引き起こすコードを生成する可能性があります
- **複雑なビジネスロジック**: ドメイン固有の複雑な計算ロジックは、要件を完全に理解させるのが難しい場合があります
- **創造的な設計**: 新規性の高いアルゴリズムや設計の創出は得意ではありません。創造的な設計には人間の判断が必要です
- **最新のライブラリやフレームワークへの対応**: 新しく登場した技術やライブラリへの対応が遅れることがあります
- **オフライン使用**: クラウド上のサーバーで推論処理を行うため、常時インターネット接続が必要です

## 実装されている機能

### 基本機能

- **対話型コード生成**: 自然言語での指示に基づき、コードを生成します
- **コード修正と編集**: 既存のコードに対する修正や最適化を提案・実行します
- **自動リファクタリング**: コードの改善提案や最適化を自動で行います
- **テストケース生成**: ユニットテストや統合テストのコードを自動生成します
- **エラー解析とデバッグ**: コードのエラーやバグを検出し、修正提案を行います
- **ドキュメント生成**: コードの説明やドキュメントを自動生成します

### 高度な機能

- **カスタムスラッシュコマンド**: ユーザーが独自のコマンドを定義し、特定のタスクを効率的に実行できます
- **サブエージェント**: 特定の機能やタスクに特化したエージェントを作成し、複雑な作業を分担させることが可能です
- **フック機能**: 特定のイベント発生時に自動的に処理を実行するフックを設定できます
- **MCP（Model Context Protocol）連携**: GitHub、Notion、Backlogなどのツールと簡単に連携し、開発環境を統合的に管理できます
- **リモートMCPサーバー連携**: 外部サービスとの連携が容易で、OAuth認証に対応しています

### CI/CD統合

- **GitHub Actionsとの統合**: CI/CDパイプラインの自動化を支援します
- **プルリクエストの自動修正**: GitHub Actionsを利用してプルリクエストを自動修正します
- **テストの自動追加**: テストケースを自動的に追加します
- **ドキュメント生成**: 自動でドキュメントを生成します

### モード機能

- **通常モード**: 各ステップで確認を求めながら作業を進めます
- **auto-acceptモード**: 自動的にステップを承認して進めます（`Shift+Tab`で切り替え可能）
- **planモード**: 実行前に計画を立てて確認します（`Shift+Tab`で切り替え可能）

### コマンド機能

- `/cost`: 現在のセッションの使用量を確認
- `/clear`: 会話履歴をクリア
- `/plan`: 計画モードに切り替え
- `/mcp`: MCPサーバーの管理
- `/reviewit`: コードレビュー機能

### VS Code拡張機能

- GUIベースのIDEでもClaude Codeを活用できます
- エディタ内での直接的なコード生成や編集が可能

## 参照したWebサイト

### 公式ドキュメント

- [Claude Code公式サイト](https://www.claude.com/ja-jp/product/claude-code)
- [Claude Code概要 - Claude Docs](https://docs.claude.com/ja/docs/agents-and-tools/claude-code/overview)
- [Claude Code セットアップガイド](https://docs.anthropic.com/ja/docs/claude-code/setup)
- [Claude Code コスト管理](https://docs.claude.com/ja/docs/claude-code/costs)
- [Claude Code セキュリティ](https://docs.claude.com/ja/docs/claude-code/security)
- [Claude Code データ使用](https://docs.claude.com/ja/docs/claude-code/data-usage)

### 日本語解説記事

- [Claude Codeとは – Claude Code JP | ＊Claude Codeの非公式ガイド](https://claudecode.jp/about-claudecode/)
- [Claude Code使用方法と料金体系徹底解説](https://www.ryoma.online/claude-code-pricing-guide/)
- [Claude Codeの使い方：Claude CodeでかんたんなWebアプリを作ってみた | CODE-PLUS](https://code-plus.jp/gp/post-7933/)
- [〖完全ガイド〗Claude Codeの設定・使い方｜CLI特化AIで効率的に開発する方法 | C-BA AI-memo](https://ai.cbagames.jp/2025/09/24/claude-code-howto/)
- [Claude Codeとは？使い方と料金！GitHub Actionsやスマホ開発について | MiraLabAI](https://miralab.co.jp/media/claude-code/)
- [Claude Code（クロード・コード）とは？開発者向けAIコーディングツールの特徴・使い方・料金を徹底解説 | ainow](https://ainow.jp/claude-code-guide/)
- [Claude Code徹底レビュー：コストと生産性を両立する次世代AIコーディング支援ツール | ainow](https://ainow.jp/claude-code-review/)

### 技術ブログ・Zenn記事

- [Claude Code がウェブ・iOS版を正式リリース！CLI版との違いなど](https://zenn.dev/tenormusica/articles/claude-code-web-release-2025-v2)
- [〖初心者向け〗Claude Code とは？インストールから使い方まで徹底解説](https://zenn.dev/takuh/articles/b846841c67f55d)
- [〖2025/10最新版〗ゼロから始めるClaude Code入門・ハンズオン](https://zenn.dev/canly/articles/2e0d115e360144)
- [Claude Code入門：ターミナルで始めるAIコーディング支援](https://zenn.dev/dotconf/articles/2025-10-08-claude-code-introduction)
- [Claude Code実践ガイド：GA版のインストールからサンドボックスPythonまで（2025年5月版）](https://zenn.dev/unikoukokun/articles/63f020b8cafbf7)
- [Claude CodeのPlanモードを駆使し、楽に品質を担保してみた - WILLGATE TECH BLOG](https://tech.willgate.co.jp/entry/2025/09/17/120000)

### 活用事例・チュートリアル

- [ウェブディレクターがClaude Codeで企業サイトを構築してみた〜工数96%削減、コード0行の衝撃体験記〜 | LUA BLANCA CONNECT](https://www.lua-branca.jp/updates/ai-website-development-experience)
- [話題のAIツール「Claude Code」でウェブサイトを自作する方法を徹底解説！](https://philipptarohiltl.com/claude-code-website-tutorial/)
- [Claude Code Windowsの最新インストール完全ガイドと活用事例比較 | Tech Home](https://rush-up.co.jp/media/claude-code-windows-install-guide-case-study/)
- [コーディングが2倍速に！エンジニアが本当に使えるコーディング特化型AIツール7選 | MD-Blog | MONSTER DIVE](https://www.monster-dive.com/blog/web_creative/20250613_002245.php)

### その他の参考資料

- [Claude Codeの使用量を完全管理！ccusageでコスト最適化を実現する方法【2025年最新版】 | キレカク | AI情報メディア](https://kirekaku.com/1055/)
- [Claude Codeの使い方完全ガイド：インストールから実践的な活用術まで – Taskhub](https://taskhub.jp/useful/claude-code-how-to-use/)
- [Claude Codeのインストール方法解説記事](https://www.room8.co.jp/claude-code-install-guide-2025/)
- [Claude Codeの特徴と活用方法に関する記事](https://www.monster-dive.com/blog/web_creative/20250613_002245.php)

## まとめ

Claude Codeは、開発者が複雑なコーディングタスクを効率的に遂行するための強力なツールです。エージェント型コーディング、多言語対応、GitHub統合、強固なセキュリティ対策などの特徴を備え、さまざまな開発シナリオでの活用が可能です。

適切なプランを選択し、システム要件を満たした上で導入することで、開発プロセスの効率化と生産性向上が期待できます。特に、非開発者でも迅速にプロトタイプを作成し、アイデアを検証する手段としても有用であり、従来の開発リソースなしにカスタムツールを構築できる可能性を秘めています。

ただし、大規模で複雑なコードベースの処理や、セキュリティ関連のコード、創造的な設計などには限界があるため、人間の判断とレビューが重要な場面では適切に使い分けることが大切です。
