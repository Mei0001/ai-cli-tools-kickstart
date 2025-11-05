# GitHub Copilot CLI

## 概要・特徴

GitHub Copilot CLIは、GitHub CopilotのAIコーディング支援機能を直接ターミナル環境で利用できるコマンドラインインターフェースです。開発者は自然言語を用いてコードの作成、デバッグ、リファクタリングなどを効率的に行うことが可能となり、IDEへの依存を減らしながらターミナル内で完結した開発体験を提供します。

### 主な特徴

#### 1. ターミナルネイティブな開発
- ターミナル内で直接Copilotの機能を活用でき、作業の流れを中断することなくコーディングが可能
- IDEへの依存を減らし、開発者の好みのエディタやツールと組み合わせて使用可能
- 自然言語での指示により、コマンドライン作業を効率化
- 開発フローの中断を最小限に抑え、シームレスな開発体験を実現

#### 2. GitHubとの深い統合
- リポジトリ、Issue、プルリクエストなどのGitHubリソースに自然言語でアクセス可能
- 既存のGitHubアカウントで認証が可能で、追加の設定が不要
- GitHubのワークフローとシームレスに連携
- リポジトリのコンテキストを理解し、適切な提案やコード生成を実行
- GitHub MCPサーバーをデフォルトで使用し、GitHubリソースへのアクセスが容易

#### 3. エージェント機能
- 複雑なタスクの計画や実行をAIが支援
- コードの生成、編集、デバッグ、リファクタリングを自動でサポート
- タスクを適切に分解し、段階的に実行
- 高レベルな指示から詳細な実装まで自動で処理
- 複数のステップを自律的に組み立てて実行するエージェント型AIとして機能

#### 4. MCPによる拡張性
- Model Context Protocol (MCP) サーバーを通じて機能拡張が可能
- GitHubのMCPサーバーをデフォルトで使用
- カスタムMCPサーバーの利用をサポートし、独自のツールやコンテキストを追加可能
- 開発環境に応じた柔軟なカスタマイズが可能
- カスタムMCPサーバーを追加することで、プロジェクト固有の機能を拡張

#### 5. 完全な制御と透明性
- すべてのアクションは実行前にプレビューされる
- ユーザーの明示的な承認なしに何も実行されない
- ファイル変更やコマンド実行のすべてが可視化される
- 組織の既存のCopilotガバナンスポリシーを自動的に継承
- 安全でないコーディングパターン（ハードコーディングされた認証情報、SQLインジェクションなど）をブロック

#### 6. 複数のAIモデルに対応
- デフォルトではClaude Sonnet 4.5が使用される
- `/model`コマンドで他のモデル（GPT-5、Gemini 2.5 Proなど）を選択可能
- Pro、Business、EnterpriseプランのプレミアムサブスクライバーはGemini 2.5 Proにもアクセス可能
- 環境変数を設定することで、異なるAIモデルを利用可能

## システム要件

### 必要な環境

- **OS**: 
  - macOS（完全サポート）
  - Linux（完全サポート）
  - Windows（WSL経由での利用が推奨、ネイティブサポートは実験的）
- **Node.js**: バージョン22以上（LTSバージョン推奨）
- **npm**: バージョン10以上
- **GitHub Copilotのサブスクリプション**: 
  - Copilot Pro
  - Copilot Pro+
  - Copilot Business
  - Copilot Enterprise
- **（Windowsの場合）**: PowerShell v6以上

## インストール方法

### macOSの場合

#### 方法1: Homebrewを使用する場合（推奨）

1. **Node.jsのインストール**
   ```bash
   brew install node@22
   ```
   
   Node.jsのバージョンを確認：
   ```bash
   node --version  # v22以上であることを確認
   ```

2. **npmのバージョン確認**
   ```bash
   npm --version   # v10以上であることを確認
   ```

3. **GitHub Copilot CLIのインストール**
   ```bash
   npm install -g @github/copilot
   ```

4. **インストール確認**
   ```bash
   copilot --version
   ```

5. **初回起動と認証**
   ```bash
   copilot
   ```
   初回起動時には、GitHubアカウントでの認証が求められます。画面の指示に従ってログインしてください。

#### 方法2: 公式サイトから直接インストール

1. **Node.jsのインストール**
   - [Node.js公式サイト](https://nodejs.org/ja/download)からmacOS版のNode.js（バージョン22以上）をダウンロードしてインストール

2. **GitHub Copilot CLIのインストール**
   ```bash
   npm install -g @github/copilot
   ```

3. **認証**
   ```bash
   copilot
   ```
   初回起動時にGitHubアカウントでの認証が求められます。

### Windowsの場合

#### 前提条件

Windows環境でのサポートは実験的であり、**WSL（Windows Subsystem for Linux）上での使用が強く推奨**されています。ネイティブなWindowsサポートは実験的機能です。

#### WSLを使用する場合（推奨）

1. **WSLのインストールとセットアップ**
   - WSL2がインストールされていることを確認
   - WSL内でLinuxディストリビューション（Ubuntu推奨）をインストール

2. **WSL内でNode.jsのインストール**
   ```bash
   # WSLターミナルを開く
   curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
   sudo apt-get install -y nodejs
   ```

3. **GitHub Copilot CLIのインストール**
   ```bash
   npm install -g @github/copilot
   ```

4. **認証**
   ```bash
   copilot
   ```

#### ネイティブWindows環境（実験的）

1. **Node.jsのインストール**
   - [Node.js公式サイト](https://nodejs.org/ja/download)からWindows版のNode.js（バージョン22以上）をダウンロードしてインストール

2. **PowerShellを管理者権限で開く**
   - Windowsキー + X → 「Windows PowerShell（管理者）」を選択

3. **GitHub Copilot CLIのインストール**
   ```powershell
   npm install -g @github/copilot
   ```

4. **インストール確認**
   ```powershell
   copilot --version
   ```

5. **認証**
   ```powershell
   copilot
   ```
   初回起動時にGitHubアカウントでの認証が求められます。

**注意**: Windows環境では、PowerShell v6以上が必要です。PowerShellのバージョンは以下のコマンドで確認できます：
```powershell
$PSVersionTable.PSVersion
```

## コスト

### サブスクリプションプラン

GitHub Copilot CLIは、GitHub Copilotの有料サブスクリプションプランに含まれています。追加の料金やAPIキーは不要です。

#### 個人向けプラン

- **Copilot Pro**
  - 月額: $10（年間サブスクリプションの場合、年額$100）
  - 対象: 個人開発者
  - GitHub Copilot CLIを含む

- **Copilot Pro+**
  - 月額: $39（年間サブスクリプションの場合、年額$390）
  - 対象: 個人開発者向けの上位プラン
  - 追加機能を含む
  - GitHub Copilot CLIを含む

#### 組織向けプラン

- **Copilot Business**
  - 月額: $19/ユーザー
  - 対象: チームや組織
  - セルフサービスのシート管理
  - GitHub Copilot CLIを含む

- **Copilot Enterprise**
  - 月額: $39/ユーザー
  - 対象: 大規模組織
  - Businessプランの全機能に加え、以下が含まれる：
    - 高度なセキュリティ
    - データ管理
    - ユーザー管理
    - 専用サポート
  - GitHub Copilot CLIを含む

### プレミアムリクエストの仕組み

- **消費単位**: Copilot CLIへの各プロンプト送信ごとに、**1つのプレミアムリクエストが消費**されます
- **クォータ**: プランごとに月次のプレミアムリクエスト許容量が設定されています
- **確認方法**: 対話型セッション内でクォータの残りを確認できます
- **追加料金**: プレミアムリクエストの上限を超えた場合の追加料金については、GitHubの公式サイトで確認してください

### 追加のコスト

- GitHub Copilot CLIの使用に追加の料金は発生しません
- GitHub Copilotのサブスクリプションに含まれています
- 追加のAPIキーや設定は不要です

## 基本的な使い方

### 基本的なコマンド

GitHub Copilot CLIは、ターミナルで`copilot`コマンドを実行することで起動します。

```bash
copilot
```

### インタラクティブモード

デフォルトでは対話型セッションが開始され、自然言語で質問やタスクの指示が可能です。

```bash
copilot
# プロンプトが表示されたら、自然言語で指示を入力
```

### プログラムモード

コマンドラインで直接プロンプトを渡すことも可能です。

```bash
copilot -p "List my open PRs" --allow-all-tools
```

`--allow-all-tools`オプションを使用すると、Copilotがファイルの変更やコマンドの実行をユーザーの承認なしに行うことができます。注意して使用してください。

### スラッシュコマンド

対話型セッション内で使用できる特別なコマンド：

- **`/model`**: 利用可能なAIモデルを選択・変更
  - 例: `/model` でモデル一覧を表示
  - デフォルト: Claude Sonnet 4.5
  - 利用可能: GPT-5、Gemini 2.5 Pro（プレミアムプラン）など

- **`/feedback`**: フィードバックの送信
  - プライベートなフィードバックアンケートへの回答
  - バグレポートの送信
  - 新機能の提案

- **`/login`**: 再認証の実行（必要に応じて）

### 特殊なコマンド構文

ターミナル内で特定のコマンドについて説明や提案を取得できます：

- **`??`**: 一般的なシェルコマンドの生成や説明
  ```bash
  ?? how to find files modified in last 7 days
  ```

- **`git?`**: Gitコマンドに特化した支援
  ```bash
  git? how to undo the last commit
  ```

- **`gh?`**: GitHub CLIコマンドの生成や説明
  ```bash
  gh? how to create a new repository
  ```

### ファイル参照

プロンプト内で`@`記号を使用して特定のファイルを参照できます：

```bash
copilot
# プロンプト内で
@src/components/Button.tsx このコンポーネントをリファクタリングしてください
```

### 基本的なワークフロー

1. **タスクの説明**
   - 自然言語でやりたいことを説明します
   - 例：「新しいAPIエンドポイントを作成してテストを追加してください」
   - 例：「オープンなプルリクエストを一覧表示してください」

2. **計画の確認**
   - Copilot CLIが計画を提示します
   - すべてのアクションがプレビューとして表示されます
   - 必要に応じて承認または修正を指示します

3. **実行**
   - ユーザーの承認後にCopilot CLIが自動的に実行します
   - 各ステップで確認を求められる場合があります

4. **レビュー**
   - 実行結果を確認します
   - 必要に応じて修正を依頼します

## 実装されている機能

### コード生成・編集機能

- **コードの生成**: 自然言語の指示からコードを生成
- **コードの編集**: 既存のコードを編集・リファクタリング
- **コードの説明**: 既存のコードの動作や目的を説明
- **複数ファイルの操作**: 複数のファイルにまたがる変更を実行

### デバッグ・メンテナンス機能

- **エラーの説明と修正**: エラーメッセージの解釈やバグの特定・修正
- **セキュリティ修正**: セキュリティ関連の修正を提案・実行
- **依存関係のアップグレード**: 依存関係の更新やアップグレードを支援
- **コードベースのメンテナンス**: プロジェクト全体のメンテナンス作業を支援

### プロジェクト管理機能

- **プロジェクトのセットアップ**: プロジェクト構造の解析、依存関係のインストール、設定のサポート
- **環境のセットアップ**: ローカル環境の設定を自動化
- **ドキュメント作成**: コードのドキュメントを生成・更新
- **テストカバレッジの向上**: 追加のテストスイートを作成

### GitHub統合機能

- **リポジトリ操作**: GitHubリポジトリの操作を自然言語で実行
- **Issue管理**: Issueの作成、更新、閲覧
- **プルリクエスト操作**: プルリクエストの作成、マージ、レビュー
- **ブランチ管理**: ブランチの作成、切り替え、マージ

### コマンド支援機能

- **コマンドの提案**: タスクを達成するための適切なコマンドを提案
- **コマンドの説明**: コマンドの機能と目的を説明
- **複雑なタスクの実行**: 複数のコマンドを組み合わせたタスクを自動で組み立てて実行

### MCP拡張機能

- **カスタムMCPサーバーの追加**: カスタムMCPサーバーを追加して機能を拡張
- **GitHub MCPサーバー**: デフォルトでGitHub MCPサーバーを使用
- **機能のカスタマイズ**: プロジェクト固有の機能を追加

## 特徴や得意なこと・苦手なこと

### 得意なこと

#### 1. コードベースのメンテナンス
- セキュリティ関連の修正
- 依存関係のアップグレード
- リファクタリング作業
- コードクリーンアップ

#### 2. ドキュメント作成
- コードのドキュメント生成
- 既存ドキュメントの更新
- APIドキュメントの作成
- READMEファイルの作成・更新

#### 3. 機能開発
- 新機能のプロトタイプ作成
- 機能要求の段階的な実装
- 小規模から中規模の機能追加

#### 4. テストカバレッジの向上
- 追加テストスイートの開発
- ユニットテストの作成
- 統合テストの作成
- エッジケースのテスト追加

#### 5. 環境のセットアップ
- ローカル環境の設定
- 依存関係のインストール
- 設定ファイルの作成
- 開発環境の構築

#### 6. コマンドの提案と説明
- 適切なコマンドの提案
- コマンドの機能と目的の説明
- 複雑なコマンドの組み合わせ

#### 7. GitHubリソースとの連携
- Issueやプルリクエストの操作
- リポジトリ情報の取得
- GitHubワークフローの自動化

### 苦手なこと

#### 1. 複雑なタスクの完全自動化
- 複雑で抽象的な指示に対する正確な応答が難しい場合がある
- 大規模な関数や複数のファイルにまたがる作業では精度が低下する可能性
- 複雑なビジネスロジックの理解には限界がある

#### 2. 最新技術への対応
- 最新のライブラリやフレームワークに関する情報が不足している場合がある
- 新しく登場した技術やツールへの対応が遅れる場合がある
- 特定のドメイン知識が必要なコードの生成や修正には限界がある

#### 3. セキュリティ上の懸念
- 生成されたコードが常に安全であるとは限らない
- セキュリティ上の脆弱性が含まれる可能性がある
- 常にレビューと検証が必要

#### 4. 大規模プロジェクトの理解
- 大規模で複雑なプロジェクト全体の文脈を完全に理解するのは難しい
- プロジェクト全体の構造を把握するのに時間がかかる場合がある

#### 5. GUI操作
- ターミナルベースのため、GUI操作が必要なタスクには適していない
- ビジュアルなデザイン作業には対応できない

#### 6. 高度なカスタマイズ
- 特定の開発環境やワークフローに強く依存する場合、適切な提案が得られないことがある
- 非常に特殊な要件には対応が難しい場合がある

## 使用例・デモ

### 例1: 新しい機能の追加

```bash
copilot
```

プロンプト例：
```
「ユーザー登録機能を追加してください。メールアドレスとパスワードで登録できるようにし、バリデーションも含めてください」
```

Copilot CLIは以下を自動的に実行します：
- 必要なファイルの作成
- データベーススキーマの更新（必要に応じて）
- バリデーションロジックの実装
- テストの作成
- 実行前にすべての変更をプレビュー表示

### 例2: バグの修正

```bash
copilot
```

プロンプト例：
```
「アプリケーションが起動時にエラーが発生しています。エラーログを確認して修正してください」
```

Copilot CLIは以下を実行します：
- エラーログの分析
- 問題の特定
- 修正の実装
- 動作確認
- 各ステップで承認を求める

### 例3: GitHubリソースへのアクセス

```bash
copilot
```

プロンプト例：
```
「オープンなプルリクエストを一覧表示して、それぞれのレビューステータスを確認してください」
```

Copilot CLIは以下を実行します：
- GitHub APIを使用してプルリクエスト情報を取得
- レビューステータスを含む詳細情報を表示
- 必要に応じてアクションを提案

### 例4: コマンドの説明と提案

ターミナル内で直接コマンドの説明を取得：

```bash
?? how to find all Python files modified in the last week
```

または、Gitコマンドについて：

```bash
git? how to undo the last commit without losing changes
```

### 例5: ドキュメントの作成

```bash
copilot
```

プロンプト例：
```
「このプロジェクトのREADMEファイルを作成してください。インストール方法、使い方、貢献方法を含めてください」
```

### 例6: セキュリティ修正

```bash
copilot
```

プロンプト例：
```
「このプロジェクトのセキュリティ脆弱性をチェックして、修正してください」
```

### 例7: 依存関係のアップグレード

```bash
copilot
```

プロンプト例：
```
「package.jsonの依存関係を最新バージョンにアップグレードしてください。破壊的変更がないか確認してください」
```

## トラブルシューティング

### よくある問題と対処法

#### 1. インストールエラー

**問題**: `npm install -g @github/copilot`でエラーが発生する

**対処法**:
- Node.jsのバージョンが22以上であることを確認: `node --version`
- npmのバージョンが10以上であることを確認: `npm --version`
- 管理者権限で実行しているか確認（Windowsの場合）
- ネットワーク接続を確認

#### 2. 認証エラー

**問題**: GitHubアカウントでの認証が失敗する

**対処法**:
- GitHubアカウントにCopilotのサブスクリプションがあることを確認
- 組織経由でCopilotにアクセスしている場合、組織の設定でCopilot CLIの使用が有効化されているか確認
- ブラウザでGitHubにログインできるか確認
- `/login`コマンドで再認証を試す

#### 3. コマンドが見つからない

**問題**: `copilot`コマンドが認識されない

**対処法**:
- インストールが正常に完了したか確認: `npm list -g @github/copilot`
- PATH環境変数にnpmのグローバルパッケージのパスが含まれているか確認
- シェルを再起動する

#### 4. Windowsでの動作問題

**問題**: Windows環境で動作しない

**対処法**:
- WSLを使用することを強く推奨
- PowerShell v6以上がインストールされているか確認
- 管理者権限で実行しているか確認

#### 5. プレミアムリクエストのクォータ不足

**問題**: プレミアムリクエストのクォータが不足している

**対処法**:
- 対話型セッション内でクォータの残りを確認
- プランのアップグレードを検討
- 使用量を確認し、必要に応じてプランを変更

## セキュリティとガバナンス

### セキュリティ機能

- **完全な制御**: すべてのファイル変更やコマンド実行は、ユーザーの明示的な承認が必要
- **アクションプレビュー**: 実行前にすべてのアクションがプレビューされる
- **安全でないパターンのブロック**: ハードコーディングされた認証情報、SQLインジェクションなどの安全でないコーディングパターンをブロック
- **ガバナンスポリシーの継承**: 組織の既存のCopilotガバナンスポリシーを自動的に継承
- **透明性**: すべてのアクションが可視化され、承認なしに実行されない

### 組織での使用

- 組織やエンタープライズ経由でCopilotにアクセスしている場合、組織の設定でCopilot CLIの使用が有効化されている必要があります
- 組織のセキュリティポリシーやガバナンス設定が自動的に適用されます
- 管理者は組織レベルでCopilot CLIの使用を制御できます

### ベストプラクティス

1. **生成されたコードのレビュー**: 生成されたコードは必ずレビューしてから本番環境に適用
2. **セキュリティチェック**: セキュリティ上の問題がないか確認
3. **段階的な開発**: 大きな変更は小さなステップに分けて実行
4. **バージョン管理**: 変更前には必ずコミットを作成
5. **クォータの管理**: プレミアムリクエストの使用量を定期的に確認

## 他のAI CLIツールとの比較

### GitHub Copilot CLI vs Claude Code

- **GitHub Copilot CLI**: GitHubとの統合が強く、GitHubリソースへのアクセスが容易。GitHub Copilotのサブスクリプションに含まれる
- **Claude Code**: AnthropicのClaudeモデルを使用。より柔軟なカスタマイズが可能。Pro/Maxプランが必要

### GitHub Copilot CLI vs Codex CLI

- **GitHub Copilot CLI**: GitHubとの統合が強く、GitHubワークフローに最適化
- **Codex CLI**: OpenAIのCodexモデルを使用。より柔軟なカスタマイズが可能。ChatGPTプランが必要

### GitHub Copilot CLI vs Cursor CLI

- **GitHub Copilot CLI**: ターミナル専用のツールとして設計され、軽量で高速
- **Cursor CLI**: Cursor IDEと統合されたツールで、IDE機能と密接に連携

## まとめ

GitHub Copilot CLIは、ターミナル環境での開発体験を大幅に向上させる強力なツールです。GitHubとの深い統合、エージェント機能、MCPによる拡張性、完全な制御と透明性などの特徴を備え、さまざまな開発シナリオでの活用が可能です。

特に、GitHub Copilotの既存ユーザーにとっては、追加の設定やAPIキーなしでターミナル内でのAI支援開発を開始できる点が大きな利点です。適切なプランを選択し、システム要件を満たした上で導入することで、開発プロセスの効率化と生産性向上が期待できます。

また、GitHubリソースへの自然言語でのアクセス機能により、コードレビューやIssue管理などのワークフローも効率化でき、GitHub中心の開発フローに最適化されたツールと言えます。

## 参考資料

### 公式ドキュメント

- [GitHub Copilot CLI 公式ページ](https://github.com/features/copilot/cli)
- [GitHub Copilot CLI リポジトリ](https://github.com/github/copilot-cli)
- [GitHub Copilot CLI の使用方法](https://docs.github.com/ja/copilot/how-tos/use-copilot-agents/use-copilot-cli)
- [GitHub Copilot CLI のインストール](https://docs.github.com/ja/enterprise-cloud@latest/copilot/how-tos/set-up/install-copilot-cli)
- [GitHub Copilot CLI について](https://docs.github.com/ja/copilot/concepts/agents/about-copilot-cli)
- [GitHub Copilot CLI の責任ある使用](https://docs.github.com/ja/enterprise-cloud@latest/copilot/responsible-use/copilot-cli)
- [CLIでのGitHub Copilotのインストール](https://docs.github.com/ja/copilot/managing-copilot/configure-personal-settings/installing-github-copilot-in-the-cli)

### NPMパッケージ

- [@github/copilot](https://www.npmjs.com/package/@github/copilot)

### チュートリアル・ガイド

- [プログラミング経験ゼロでもOK！GitHub Copilot CLI入門 - Feel Flow Inc.](https://feelflow.co.jp/report/github-copilot-cli/)
- [2025年最新 GitHub Copilot CLI徹底解説 - Saiteki AI](https://saiteki-ai.com/development/ai-coding/github-copilot-cli-2/)
- [GitHub Copilot CLI衝撃リリース！ターミナルで動くAIエージェントの全貌 - SmartScope](https://smartscope.blog/github-copilot-cli-release-2025/)

### 記事・ブログ

- [GitHub Copilot CLI のパブリックプレビュー開始 - 窓の杜](https://forest.watch.impress.co.jp/docs/news/2050188.html)
- [GitHub Copilotが変革する開発現場の現実：GitHub Copilot 使い方完全ガイド](https://kairilab.com/2025/08/24/github-copilot%E3%81%8C%E5%A4%89%E9%9D%A9%E3%81%99%E3%82%8B%E9%96%8B%E7%99%BA%E7%8F%BE%E5%A0%B4%E3%81%AE%E7%8F%BE%E5%AE%9F%EF%BC%9Agithub-copilot-%E4%BD%BF%E3%81%84%E6%96%B9%E5%AE%8C%E5%85%A8%E3%82%AC/)
- [GitHub Copilot完全ガイド｜使い方・料金・活用法・導入リスクまで徹底解説](https://www.luft.co.jp/media/github-copilot/)

### 動画・チュートリアル

- [GitHub Copilot CLI: Install & Set Up on Mac, Windows & Linux (Step-by-Step Guide!) - YouTube](https://www.youtube.com/watch?v=G-XdaGst-ro)

### コミュニティ・フォーラム

- [GitHub Copilot CLI リポジトリのIssues](https://github.com/github/copilot-cli/issues)
- [GitHub Discussions](https://github.com/github/copilot-cli/discussions)
