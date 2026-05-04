# WASSYOI / Portfolio

WASSYOI（工房）のポートフォリオサイト。GitHub Pages 配信前提の静的サイトです。

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

- 本番 URL: `index.html` 内に直書き（`jsf-volunteer2026.vercel.app` / `hoyahho-volunteer.vercel.app`）
- 掲載スクリーンショット: `assets/jsf/` / `assets/hoya/` のファイルを差し替え
- Hero コピー・プロジェクト概要: `index.html` の該当セクション
- 配色・タイポグラフィ・コンポーネント: `matsuri.css` のトークン（`--m-red`, `--m-mustard`, `--m-teal` など）

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
