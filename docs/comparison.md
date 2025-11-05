# AI CLIツール比較表

## 比較項目

| ツール名 | 機能 | 特徴 | 価格 | 対応OS | 備考 |
|---------|------|------|------|--------|------|
| Claude Code | コード生成・編集・リファクタリング・テスト生成・デバッグ支援 | AnthropicのClaudeモデル、エージェント型コーディング、GitHub統合、プロジェクト全体の理解 | Pro: $20/月、Max: $100-200/月 | macOS, Linux, Windows(WSL) | 多言語対応、VS Code拡張機能あり |
| Codex CLI | コード生成・編集・実行・テスト自動化・デバッグ支援 | OpenAI、ローカル実行、サンドボックスモード、オープンソース | ChatGPT Plus($20)以上 | macOS, Linux, Windows(WSL) | オープンソース、プライバシー保護 |
| Gemini CLI | コード生成・レビュー・実行支援・ファイル操作・Web検索 | Google Geminiモデル、100万トークンコンテキスト、マルチモーダル対応、MCPサポート | 無料枠あり、従量課金あり | macOS, Linux, Windows(WSL) | オープンソース、Google検索統合 |
| Cursor CLI | コード生成・レビュー・変更・ドキュメント化 | IDE統合、MCPサポート、ルールシステム、セッション管理 | ベータ版（無料） | macOS, Linux, Windows(WSL) | Cursor IDEと統合、ベータ版 |
| GitHub Copilot CLI | コード生成・デバッグ・リファクタリング・GitHub統合 | GitHubとの深い統合、エージェント機能、MCPサポート、完全な制御 | Copilot Pro($10)以上 | macOS, Linux, Windows(WSL) | GitHub統合が強力 |

## 詳細比較

### 機能面での比較

#### コード生成・編集
- **Claude Code**: エージェント型で自律的に複数ステップを実行
- **Codex CLI**: 自然言語からコード生成、ローカル実行重視
- **Gemini CLI**: 大規模コンテキスト（100万トークン）で大規模プロジェクト対応
- **Cursor CLI**: IDE統合でGUIとCLIの両方で利用可能
- **GitHub Copilot CLI**: GitHubリソースとの統合が強力

#### セキュリティ・プライバシー
- **Claude Code**: ローカル環境での動作、プライバシー保護
- **Codex CLI**: サンドボックスモード、ローカル実行、コードは送信されない
- **Gemini CLI**: オープンソース、Google Cloud統合オプション
- **Cursor CLI**: ベータ版のためセキュリティ保護は進化中
- **GitHub Copilot CLI**: 組織のガバナンスポリシー継承、安全でないパターンをブロック

#### 統合・拡張性
- **Claude Code**: GitHub Actions統合、MCP連携
- **Codex CLI**: VSCode/Cursor拡張機能、カスタマイズ性が高い
- **Gemini CLI**: MCPサポート、Google検索統合、カスタムMCPサーバー対応
- **Cursor CLI**: Cursor IDEと統合、MCPサポート、ルールシステム
- **GitHub Copilot CLI**: GitHub MCPサーバー標準搭載、カスタムMCPサーバー対応

### 価格面での比較

| ツール | 無料枠 | 最低プラン | 中級プラン | エンタープライズ |
|--------|--------|------------|------------|------------------|
| Claude Code | ❌ | $20/月 (Pro) | $100-200/月 (Max) | 問い合わせ |
| Codex CLI | ❌ | $20/月 (ChatGPT Plus) | $200/月 (ChatGPT Pro) | 契約制 |
| Gemini CLI | ✅ | 無料枠あり | 従量課金 | Enterprise版あり |
| Cursor CLI | ✅ | ベータ版無料 | 未定 | 未定 |
| GitHub Copilot CLI | ❌ | $10/月 (Pro) | $19/月 (Business) | $39/月 (Enterprise) |

### 対応OSでの比較

- **macOS**: 全ツール対応 ✅
- **Linux**: 全ツール対応 ✅
- **Windows**: 
  - Claude Code: WSL推奨、ネイティブも可能
  - Codex CLI: WSL推奨、実験的なネイティブ対応
  - Gemini CLI: WSL推奨
  - Cursor CLI: WSL推奨
  - GitHub Copilot CLI: WSL推奨、実験的なネイティブ対応

### 使いやすさでの比較

#### 初心者向け
- **Gemini CLI**: 無料枠あり、オープンソース、導入が容易
- **Cursor CLI**: ベータ版で無料、IDE統合で使いやすい
- **GitHub Copilot CLI**: GitHubユーザーには統合が自然
- **Codex CLI**: ChatGPTプラン利用者には親しみやすい
- **Claude Code**: 高機能だが設定が必要

#### 上級者向け
- **Claude Code**: 高度なカスタマイズ、エージェント機能
- **Codex CLI**: オープンソース、カスタマイズ性が高い
- **Gemini CLI**: MCP拡張、大規模プロジェクト対応
- **Cursor CLI**: ルールシステム、セッション管理
- **GitHub Copilot CLI**: GitHubワークフロー統合

### 推奨用途

- **Claude Code**: エンタープライズ開発、大規模プロジェクト、複雑なタスク
- **Codex CLI**: オープンソース開発、プライバシー重視、カスタマイズ重視
- **Gemini CLI**: 大規模コードベース、Googleサービス利用者、無料で試したい場合
- **Cursor CLI**: Cursor IDEユーザー、ベータ機能を試したい場合
- **GitHub Copilot CLI**: GitHub中心の開発、チーム開発、GitHubワークフロー統合

