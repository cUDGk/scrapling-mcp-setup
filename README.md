# Scrapling MCP セットアップガイド

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![MCP](https://img.shields.io/badge/MCP-Model_Context_Protocol-8B5CF6?style=for-the-badge)](https://modelcontextprotocol.io/)
[![Scrapling](https://img.shields.io/badge/Scrapling-v0.4.2-E65100?style=for-the-badge)](https://github.com/D4Vinci/Scrapling)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

## 概要

このリポジトリは、[Scrapling](https://github.com/D4Vinci/Scrapling) を Claude Code の MCP サーバーとしてセットアップする手順をまとめたドキュメントです。

**Scrapling** は [Karim Shoair (D4Vinci)](https://github.com/D4Vinci) 氏が開発した Python 製の Web スクレイピングライブラリで、[BSD 3-Clause License](https://github.com/D4Vinci/Scrapling/blob/main/LICENSE) のもとで公開されています。

### Scrapling の主な特徴

- **アンチボットバイパス**: Cloudflare、WAF 等の保護を回避するステルスモード
- **適応型スクレイピング**: サイト構造の変更に自動対応
- **AI 統合**: LLM との連携を前提とした設計
- **MCP サポート**: v0.4.x 以降、MCP サーバー機能を内蔵

## 利用可能なツール

| ツール名 | 説明 |
|---|---|
| `fetch` | 単一 URL を取得（標準モード） |
| `get` | 単一 URL を取得（軽量モード） |
| `stealthy_fetch` | 単一 URL を取得（ステルスモード、アンチボット回避） |
| `bulk_fetch` | 複数 URL を一括取得（標準モード） |
| `bulk_get` | 複数 URL を一括取得（軽量モード） |
| `bulk_stealthy_fetch` | 複数 URL を一括取得（ステルスモード） |

## インストール

### 1. Scrapling のインストール

```bash
pip install "scrapling[all]"
```

### 2. ブラウザエンジンのインストール

```bash
scrapling install
```

> このコマンドにより、ステルスモードで使用するブラウザエンジン（Playwright ベース）がインストールされます。

## Claude Code への MCP 登録

Claude Code の設定ファイル（`settings.json`）に以下を追加します:

```json
{
  "mcpServers": {
    "ScraplingServer": {
      "command": "python",
      "args": ["-m", "scrapling.mcp"]
    }
  }
}
```

登録後、Claude Code を再起動すると MCP ツールとして利用可能になります。

## バージョン情報

- Scrapling: **v0.4.2**
- MCP サポート: v0.4.x 以降

## 公式ドキュメント

- GitHub: https://github.com/D4Vinci/Scrapling
- ドキュメント: https://scrapling.readthedocs.io/

## Attribution

このリポジトリは以下のオープンソースプロジェクトのセットアップ手順をまとめたものです:

- **[Scrapling](https://github.com/D4Vinci/Scrapling)** -- Python 製の Web スクレイピングライブラリ。[Karim Shoair (D4Vinci)](https://github.com/D4Vinci) 氏によるプロジェクト。BSD 3-Clause ライセンス。
- **[MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk)** -- Model Context Protocol の公式 Python 実装。Anthropic による [MCP 仕様](https://modelcontextprotocol.io/) に基づく。

---

## ライセンス

[MIT License](LICENSE) -- Copyright (c) 2026 cUDGk
