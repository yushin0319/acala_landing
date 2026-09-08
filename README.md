# Acala Landing Page

サバイバルゲームフィールド「Acala」（奥能登）のランディングページ。ビルドツール無しの静的サイト。GitHub description: 「それっぽいLP」。

> 公開はしていない（GitHub Pages 無効）。ローカルで `index.html` を開いて確認する。

## スタック

- HTML / CSS / JavaScript（Vanilla、ビルドステップなし）
- jQuery 3.7.1（CDN: code.jquery.com、SRI 付き）
- Slick Carousel 1.8.1（CDN: jsDelivr、CSS + JS、SRI 付き）

## 構成

```
index.html        ページ本体
css/styles.css    スタイル
js/script.js      Slick 初期化ほか
images/           001–012.jpg/png / logo.png / main.png / title.png
```

## ページ構成

| セクション | 見出し | 内容 |
|-----------|--------|------|
| `header` | （ロゴのみ） | `position: sticky` の固定ヘッダー。ナビゲーションリンクは無い |
| `.background` | — | メインビジュアル。`#mv` に CSS `@keyframes fade`（1.2s）でフェードイン、`#title` を重ねる |
| `.about` | CONCEPT | フィールドのコンセプト紹介 |
| `.gallery` | GALLERY | Slick スライダーによる写真ギャラリー（9 枚、`slidesToShow: 3` / centerMode / variableWidth / autoplay） |
| `.contact` | ご連絡はこちら | お問い合わせフォーム（氏名 / メールアドレス / お問い合わせ内容） |

## 既知の制約

- **お問い合わせフォームは動作しない**。`<form>` 要素が無く `action` も未設定で、`<input type="submit">` を押しても送信先が無い。表示のみのモックアップ
- `js/script.js` の `DOMContentLoaded` ハンドラは `header img`（ロゴ）の `opacity` を 1 にしているが、CSS 側で既に `header { opacity: 1 }` が効いており実質 no-op。メインビジュアルのフェードインは CSS アニメーション側で行っている

## 開発

ビルド不要。

```bash
start index.html          # Windows でそのまま開く

# もしくは簡易サーバー経由（CDN 読み込みがあるため要ネットワーク）
python -m http.server 8000
```

## CI

- PR レビュー: `.github/workflows/gemini-review.yml`
- CodeQL: `.github/workflows/codeql.yml`
- Dependabot patch/minor は `dependabot-automerge.yml` で auto-merge
