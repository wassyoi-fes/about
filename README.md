# WASSYOI

お祭工房 WASSYOI のサイト。営業資料 QR の遷移先として、お祭主催者・実行委員会向けに事例と問い合わせ導線をまとめた、GitHub Pages 配信前提の静的サイトです。

`index.html` 一枚 + `matsuri.css`（デザインシステム）+ `portfolio.css`（このサイト固有のレイアウト） + `assets/` の構成で、ビルド不要・そのまま配信できます。

## 構成

```
wassyoi-portfolio/
├── index.html          ポートフォリオ本体（1 ページ）
├── matsuri.css         WASSYOI Design System（デザイントークン・コンポーネント）
├── portfolio.css       このサイト固有のレイアウト
├── assets/
│   ├── jsf/            定禅寺ジャズフェス用スクリーンショット
│   └── hoya/           ほやっほー祭用スクリーンショット
└── .nojekyll           GitHub Pages の Jekyll 処理を無効化
```

## ローカル確認

```bash
# 任意の静的サーバーで
python -m http.server 8000
# → http://localhost:8000
```

## GitHub Pages へのデプロイ

1. GitHub に新規リポジトリ（例: `chifukomu/wassyoi-portfolio`）を作成
2. このディレクトリをそのまま push
3. リポジトリの **Settings → Pages** → Source を `Deploy from a branch` に、ブランチを `main` / フォルダを `/ (root)` に設定
4. 数分後 `https://<user>.github.io/wassyoi-portfolio/` で公開

カスタムドメインを使う場合は `CNAME` ファイルをルートに追加。

## 編集ポイント

- 事例の追加: `index.html` の `.case-grid` 内に `<article class="case">`（または `case case--reverse`）をもう 1 件複製し、画像・日付・地名・タイトル・本文・サイト URL を差し替える
- 掲載スクリーンショット: `assets/<slug>/` にカバー画像を 1 枚追加
- お問い合わせ先: `index.html` の `mailto:` 部分を実際のメールアドレスに差し替え
- 配色・タイポグラフィ・コンポーネント: `matsuri.css` のトークン（`--m-red`, `--m-mustard`, `--m-teal` など）

## トーンの方針

このサイトは営業資料 QR からの遷移先。エンジニア向けの情報（GitHub・技術スタック・パス・バージョン番号）は出さず、お祭主催者・実行委員会・自治体担当者が「WASSYOI に頼むと何ができるか」をすぐに掴める表現に揃える。

## デザインシステム

`matsuri.css` は WASSYOI Design System (Matsuri Direction) — 紙コラージュ風の祭ビジュアル。
ペーパー地・マスキングテープ・ハーフトーン・鉢巻ストリップ・スタンプ風シールなどを CSS で実装。

主要トークン:

| 用途 | 変数 | 値 |
| --- | --- | --- |
| 主役の赤（朱） | `--m-red` | `#D63B1F` |
| 補色マスタード | `--m-mustard` | `#E8B84A` |
| ジャズフェス用ティール | `--m-teal` | `#1E7A7A` |
| 紙の地色 | `--m-cream` / `--m-paper` | `#FBF5E9` / `#F7EDD8` |
| 墨 | `--m-ink` | `#1A1614` |

ディスプレイ書体は **Bricolage Grotesque**、本文は **Zen Kaku Gothic New**、機械可読ラベルは **JetBrains Mono**（すべて Google Fonts から読込）。
