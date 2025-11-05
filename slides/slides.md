---
marp: true
theme: default
paginate: true
header: 'AI CLI Tools Kickstart Guide'
footer: '© 2025'
style: |
  section {
    font-family: 'Hiragino Sans', 'Hiragino Kaku Gothic ProN', 'Noto Sans JP', sans-serif;
  }
---

<!-- _class: title -->

# AI CLI Tools Kickstart Guide

生成AI界隈で話題のAI CLIツールについて
初学者向けに説明・比較するキックオフ資料

---

## 目次

1. Claude Code
2. Codex
3. Gemini CLI
4. Cursor CLI
5. GitHub Copilot CLI
6. その他のAI CLIツール
7. 比較とまとめ

---

<!-- _class: split -->

## Claude Code

### 概要・特徴

[ここにClaude Codeの概要と特徴を記載]

### インストール方法

[ここにインストール手順を記載]

### 基本的な使い方

[ここに基本的な使い方のチュートリアルを記載]

---

<!-- _class: split -->

## Codex

### 概要・特徴

[ここにCodexの概要と特徴を記載]

### インストール方法

[ここにインストール手順を記載]

### 基本的な使い方

[ここに基本的な使い方のチュートリアルを記載]

---

<!-- _class: split -->

## Gemini CLI

### 概要・特徴

[ここにGemini CLIの概要と特徴を記載]

### インストール方法

[ここにインストール手順を記載]

### 基本的な使い方

[ここに基本的な使い方のチュートリアルを記載]

---

<!-- _class: split -->

## Cursor CLI

### 概要・特徴

[ここにCursor CLIの概要と特徴を記載]

### インストール方法

[ここにインストール手順を記載]

### 基本的な使い方

[ここに基本的な使い方のチュートリアルを記載]

---

<!-- _class: split -->

## GitHub Copilot CLI

### 概要・特徴

[ここにGitHub Copilot CLIの概要と特徴を記載]

### インストール方法

[ここにインストール手順を記載]

### 基本的な使い方

[ここに基本的な使い方のチュートリアルを記載]

---

## その他のAI CLIツール

Claude Code、Codex CLI、Gemini CLI、Cursor CLI、GitHub Copilot CLI以外のAI特化型CLIツール

---

## Amazon Q Developer CLI

**主な特徴**:
- AWSサービスとの統合が強力
- エージェント型のコーディング体験
- 運用のトラブルシューティング支援
- ローカルファイルの読み書きが可能

**主な機能**:
- エージェント型コーディング体験
- AWSリソースのクエリ
- 自動デバッグ
- 運用のトラブルシューティング支援

---

## Grok CLI

**主な特徴**:
- オープンソース（MITライセンス）
- 自然言語による直感的な操作
- 複数のAIモデルに対応
- 導入が容易で学習コストが低い

**主な機能**:
- 自然言語による操作
- 複数のAIモデル対応
- ファイル操作
- シェルコマンドの実行

```bash
# インストール
npm install -g grok-cli
# または
pip install grok-cli
```

---

## Cline

**主な特徴**:
- 自律型AIエージェント
- 日本語対応
- Git操作の自動化
- プロジェクト規約の定義が可能

**主な機能**:
- コード生成
- テスト作成
- リファクタリング
- パッケージ管理
- Git操作の自動化

VS Code拡張機能としてインストール

---

## Factory Droids

**主な特徴**:
- 軽量・高速（GUI不要）
- CI/CDパイプラインに統合可能
- 高い自動化能力
- Terminal-Benchで高い性能を記録（58.8%）

**主な機能**:
- 自然言語によるコード生成
- 自動化
- 高性能処理

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

## ツールの分類

### 開発支援ツール
- Amazon Q Developer CLI
- Grok CLI
- Cline
- Factory Droids

### コード解析ツール
- scg-cli

### MLモデル管理ツール
- MLModelCI

### データセット作成ツール
- ShIOEnv

### マルチモーダル処理ツール
- i-Code Studio

---

## 比較表

| ツール名 | 機能 | 特徴 | 価格 | 対応OS | 備考 |
|---------|------|------|------|--------|------|
| Claude Code | [機能を記載] | [特徴を記載] | [価格を記載] | [対応OSを記載] | [備考を記載] |
| Codex | [機能を記載] | [特徴を記載] | [価格を記載] | [対応OSを記載] | [備考を記載] |
| Gemini CLI | [機能を記載] | [特徴を記載] | [価格を記載] | [対応OSを記載] | [備考を記載] |
| Cursor CLI | [機能を記載] | [特徴を記載] | [価格を記載] | [対応OSを記載] | [備考を記載] |
| GitHub Copilot CLI | [機能を記載] | [特徴を記載] | [価格を記載] | [対応OSを記載] | [備考を記載] |

---

## まとめ

- 各AI CLIツールは異なる目的と特徴を持っています
- プロジェクトの要件や開発環境に応じて適切なツールを選択することが重要です
- 開発支援、コード解析、MLモデル管理など、用途に応じて使い分けましょう

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

