---
layout: default
title: Quick try | CommitPilot
permalink: /quick-try/
description: 1分で「チャット→PR」を体験。Free: 1 file / 512KB / PR-first / 危険パス拒否。
last_updated: 2025-10-19
---

# Quick try（1分）

CommitPilot は、**チャットだけで GitHub に PR を作る**ツールです。  
Free モードは **1ファイル / 512KB / PR-first / 危険パス拒否**。まずは1分で体験を。

- 開く → **Open in ChatGPT**（あなたのGPTリンク）  
- ドキュメント → [トップ](/) / [Privacy](/privacy/) / [Terms](/terms/)

---

## 前提（最小）
- GitHub アカウントにログイン済み
- （初回のみ）GPT で **GitHub を OAuth 接続（`repo`）**
- 触るリポ（例：`hirohirohotate-sketch/Nestly`）があること  
  - 推奨：`main` は **ブランチ保護（PR必須）**

---

## A. 最短スモーク（READMEに1行追記 → PR）

下の2つを**まとめて**チャットに貼って「コミットして → PR作って」と言うだけ。

````text
```commit
# owner/repo を変える場合はここで指定。省略時はGPT側のDefaultsが使われます。
owner=hirohirohotate-sketch
repo=Nestly
base=main
branch=ai-bot/quick-smoke
path=README.md
message=chore: smoke test from CommitPilot
mode=append
```
```md
✅ CommitPilot smoke test — {{now}}.
```
