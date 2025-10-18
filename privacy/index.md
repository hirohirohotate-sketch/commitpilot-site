---
layout: default
title: Privacy Policy | CommitPilot
description: CommitPilot (Public Beta) privacy policy
permalink: /privacy/
last_updated: 2025-10-18
---

# CommitPilot プライバシーポリシー（Public Beta）

最終更新日：2025-10-18

本ポリシーは、**CommitPilot**（以下「本サービス」）が、ChatGPT の **Actions** 機能を介して GitHub API を利用する際の個人情報・データの取り扱いについて定めるものです。

> **要点（要約）**
> - 送信するのは、あなたが指示した**最小限の実行データ**（ファイル内容・パス・コミットメッセージ等）に限ります。  
> - 当方のサーバーに**会話やコード、トークンを保存しません**。OAuth トークンは ChatGPT で管理され、当方はアクセスできません。  
> - 実行は **GitHub** に対して行われ、GitHub 側での取扱いは GitHub のポリシーに従います。  
> - PR には監査用の短いフッター（実行者・時刻・操作ID）を付ける場合があります。  
> - 危険パス（`.env`/`.ssh`/`**/secrets/**`/`.github/workflows/**`/`..`など）は**拒否**します。

---

## 1. 適用範囲
- 本サービスの **Public Beta** 期間に、ChatGPT 上で本サービスを利用する場合に適用されます。
- 本サービス自体はサーバーを持たず、実行は ChatGPT の Actions と **GitHub API** を通じて行われます。

## 2. 送信・処理するデータ
本サービスは、あなたの指示を実行する目的で、以下の**最小限**のデータを **GitHub** へ送信します。

| 区分 | 具体例 | 送信先 |
|---|---|---|
| ファイル関連 | ファイル内容（テキスト）、ファイルパス、モード（上書き/追記） | GitHub API |
| コミット関連 | コミットメッセージ、ターゲットブランチ名、ベースブランチ名、対象リポジトリ | GitHub API |
| PR関連 | PR タイトル/本文（テンプレ適用時を含む）、ブランチ情報 | GitHub API |
| 監査情報 | 実行者（取得可能な範囲）、JST 時刻、使用した操作 ID（operationIds） | GitHub（PR本文に記載） |

※ **バイナリや大容量**の送信はサポートしません（テキスト合計 512KB まで）。

## 3. 収集・保存しないデータ
当方のサーバーでは以下を**保存・収集しません**。
- 会話内容、コード、コミット内容、PR 内容  
- OAuth トークン、パスワード、個人情報  
- 行動トラッキングのための Cookie 等

> OAuth トークンは ChatGPT の Actions 機構で管理され、当方は閲覧・保管できません。

## 4. 第三者提供
- 実行のために **GitHub** へデータを送信します。GitHub 側での保管・処理は GitHub のポリシーに従います。
- 将来、Pro/Gateway 機能を有効化する場合は、決済事業者（例：Stripe/Lemon Squeezy）との連携が発生することがあります。その際は本ポリシーを更新し、取扱いを明示します。

## 5. セキュリティと拒否ルール
- 危険ファイル/パスは実行前に**拒否**します（例：`.env*`、`.ssh*`、`**/secrets/**`、`.github/workflows/**`、`..` を含むパス、先頭がドットの隠しファイル）。  
- `main` 直 push は既定で行わず、**ブランチ作成→PR** のフローを優先します（明示確認がある場合のみ例外）。  
- サイズ上限：1 回のリクエストは**テキスト 512KB 以内**。  
- 競合（409）は最新 `sha` で 1 回リトライし、失敗時は代替ブランチを提案します。

## 6. 監査（PR フッター）
透明性のため、PR 本文に以下を付与することがあります。
```
---
Audit
- actor: <取得可能な範囲での実行者識別>
- time: <JST ISO 8601>
- actions: getBranch, createRef, getFile, putFile, createPR
```

## 7. Cookie / アナリティクス
- 本サービスは独自の Cookie や解析タグを使用しません。  
- GitHub Pages / GitHub / ChatGPT 側でのログ・Cookie 等の取扱いは各提供元のポリシーに従います。

## 8. 未成年の利用
本サービスは開発者向けです。13 歳未満（または各地域の同等年齢）の方は利用しないでください。

## 9. ユーザーの権利
- 送信前に内容を確認・修正できます。送信後は GitHub 上で差分・履歴を確認・管理してください。  
- 本サービスはローカル保存を行わないため、当方に削除要求を行う対象データは基本的に存在しません。

## 10. 政策の変更
運用や機能の変更に応じて本ポリシーを更新することがあります。更新日はページ上部の「最終更新日」に表示します。

## 11. お問い合わせ
- 運営：<組織名またはハンドル>
- 連絡先：<お問い合わせメールアドレス>
- サイト：<Web サイト/プロフィール URL>

---

# CommitPilot Privacy Policy (Public Beta)

**Last updated:** 2025-10-18

This policy describes how **CommitPilot** (“the Service”) handles data when using GitHub via ChatGPT **Actions**.

> **At a glance**
> - We send only the **minimum data** needed to fulfill your request (file contents, path, commit message, etc.).  
> - We **do not store** your code, conversations, or tokens on our servers. OAuth tokens are managed by ChatGPT Actions.  
> - Execution happens against **GitHub**; their policies apply on their side.  
> - A short audit footer (actor / JST timestamp / operation IDs) may be added to PRs.  
> - We block dangerous paths (e.g., `.env`, `.ssh`, `**/secrets/**`, `.github/workflows/**`, path traversal).

## 1. Scope
- Applies when you use the Service during **Public Beta** inside ChatGPT.  
- The Service has no standalone server; it operates through ChatGPT Actions and **GitHub API**.

## 2. Data processed / sent
We send the following **minimum** data to **GitHub** to execute your request:

| Category | Examples | Destination |
|---|---|---|
| File | File contents (text), file path, mode (overwrite/append) | GitHub API |
| Commit | Commit message, target branch, base branch, repository | GitHub API |
| Pull Request | PR title/body (including template), branch info | GitHub API |
| Audit | Actor (when available), JST timestamp, operation IDs | GitHub (PR body) |

> Binary/large payloads are not supported. Text total per request ≤ **512 KB**.

## 3. Data we do **not** store
We do **not** store on our servers:
- Conversations, code, commit/PR contents  
- OAuth tokens, passwords, personal data  
- Tracking cookies or analytics

> OAuth tokens are handled by ChatGPT Actions; we cannot access or retain them.

## 4. Third parties
- We send requests to **GitHub**; storage and handling on their side follow GitHub’s policies.  
- If Pro/Gateway features are enabled in the future, we may integrate with payment providers (e.g., Stripe/Lemon Squeezy). Any such change will be reflected here.

## 5. Security & denials
- We **deny** dangerous files/paths (e.g., `.env*`, `.ssh*`, `**/secrets/**`, `.github/workflows/**`, path traversal `..`, leading dotfiles).  
- **PR-first:** no direct push to `main` unless explicitly confirmed.  
- Max request size: **512 KB** (text).  
- On conflict (409), we fetch the latest `sha` once and retry; otherwise propose an alternative branch.

## 6. Audit (PR footer)
We may append:
```
---
Audit
- actor: <available identifier>
- time: <JST ISO 8601>
- actions: getBranch, createRef, getFile, putFile, createPR
```

## 7. Cookies / Analytics
- The Service does not use its own cookies or analytics.  
- GitHub Pages / GitHub / ChatGPT may have their own logs/cookies per their policies.

## 8. Children’s privacy
The Service targets developers. Do not use if you are under the minimum age in your jurisdiction (e.g., 13).

## 9. Your rights
- You can review/modify data **before** sending. After execution, manage history on GitHub (diffs, commits).  
- We keep no server-side copies; therefore, deletion requests generally do not apply to us.

## 10. Changes to this policy
We may update this policy. The **Last updated** date at the top reflects the current version.

## 11. Contact
- Operator: CommitPilot Project (hirohirohotate-sketch)
- Email: hirohirohotate@gmail.com
- Site: https://hirohirohotate-sketch.github.io/commitpilot-site/
