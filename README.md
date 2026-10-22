# app-support

Toshihiro Funamoto（tofu76）が個人で開発しているアプリの、サポートページ・プライバシーポリシー・利用規約と、ご意見・お問い合わせの窓口（Issue）を置く公開リポジトリです。

- 公開先: https://tofu76.github.io/app-support/
- ご意見・お問い合わせ: https://github.com/tofu76/app-support/issues/new/choose

Issue の内容は公開されます。名前・連絡先・ID やパスワードなどは書かないでください。土曜・日曜に確認してお返事します（平日はお返事できません）。

## アプリ

| アプリ | ページ | フォーム（ラベル） |
| --- | --- | --- |
| あしもりん | [サポート](https://tofu76.github.io/app-support/asimorin/support.html)・[プライバシーポリシー](https://tofu76.github.io/app-support/asimorin/privacy.html)・[利用規約](https://tofu76.github.io/app-support/asimorin/terms.html) | `feedback-asimorin.yml`（`asimorin`） |
| No梗塞 | [サポート](https://tofu76.github.io/app-support/nokosoku/support.html)・[プライバシーポリシー](https://tofu76.github.io/app-support/nokosoku/privacy.html) | `feedback-nokosoku.yml`（`nokosoku`） |
| アスデミック | [サポート](https://tofu76.github.io/app-support/asudemic/support.html)・[プライバシーポリシー](https://tofu76.github.io/app-support/asudemic/privacy.html) | `feedback-asudemic.yml`（`asudemic`） |

## 構成

GitHub Pages の Jekyll で、Markdown から HTML を作ります（ビルドの設定は不要）。ページの文面の正本は、このリポジトリの Markdown です。

```
_config.yml                  サイトの設定（baseurl: /app-support）
_data/apps.yml               アプリの一覧。トップ・各アプリのトップ・お問い合わせの欄はここから作る
_layouts/default.html        共通のレイアウト（ライト・ダーク対応）
_includes/app_index.html     各アプリのトップの本文
_includes/feedback.html      ご意見・お問い合わせの欄（apps.yml の form から Issue の URL を作る）
assets/style.css
index.md                     アプリの一覧
<id>/index.md                アプリのトップ（{% include app_index.html %} だけ）
<id>/support.md など          アプリのページ。front matter に app と permalink を書く
.github/ISSUE_TEMPLATE/      アプリごとのフォームと config.yml
```

URL は `https://tofu76.github.io/app-support/<id>/<ページ>.html` です。アプリの中やストアに書いた URL が変わらないよう、公開したページの `permalink` は変えないでください。

## アプリを足す

1. `_data/apps.yml` に 1 件足す（`id`・`name`・`summary`・`platforms`・`form`・`pages`）。
2. `<id>/` フォルダを作り、`index.md` と、`pages` に書いたページの Markdown を置く。各ページの front matter に次を書く。
   ```yaml
   ---
   app: <id>
   title: サポート
   permalink: /<id>/support.html
   ---
   ```
   お問い合わせの欄を出すところに `{% include feedback.html %}` を書く。
3. `.github/ISSUE_TEMPLATE/feedback-<id>.yml` を作る（`labels: ["<id>"]`）。`config.yml` にサポートページへのリンクを足す。
4. ラベル `<id>` を作る（`gh label create <id> --repo tofu76/app-support`）。無いラベルは Issue に付かない。
5. 上の「アプリ」の表に足す。

## 注意

- No梗塞のアプリは、`feedback-nokosoku.yml` を事前入力つき（`kind`・`content`・`device`・`title`）で開きます。項目の id と `kind` の選択肢の文字列を変えないでください。
- 旧リポジトリ `tofu76/nokosoku-support` のページは、ここへの転送にしてあります。旧リポジトリのフォーム（`feedback.yml`）は、No梗塞のアプリが新しい URL に変わるまで残します。

## ページの公開（GitHub Pages）

Settings › Pages › Build and deployment › Source を「Deploy from a branch」にし、Branch を `main` / `(root)` にします。push すると数分で反映されます。
