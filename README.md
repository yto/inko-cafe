# inko-cafe（ワカケホンセイインコカフェ）

架空のカフェのサイト。**Claude Code の合宿**で「動物カフェのサイトを作る」というお題が出て作ったもの。

- **公開URL**: https://wakahoncafe.pages.dev/
- **設定**: 林試の森公園のオープンカフェ。ワカケホンセイインコが集まる

**ククデ会スライドの「いろいろ作れます」のページ**で、サムネイルの作例のひとつとして見せている。そのため使い捨てにせず残している（他の作例は使い捨て）。

## 公開リポジトリにしている

**作例なので中身を見てもらえるほうがよい**と判断した。Public にする前に次を確かめてある。

- **秘密情報が無いこと**（APIキー・トークン・パスワードのたぐいを扱っていない。`.wrangler/` は `.gitignore` 済み）
- **個人情報が無いこと**（写真に GPS 情報なし）
- **画像のライセンス**。Wikimedia Commons の CC 系で、**作者名とライセンスを `index.html` に明記**してある

⚠ **`.wrangler/` は必ず無視する。** ここに `wrangler-account.json` が作られ、**Cloudflare のアカウントID とメールアドレスが入る**。初回コミットで一度巻き込んだ（GitHub に上げる前に履歴ごと作り直した）。

## 構成

静的サイト1枚だけ。ビルドもサーバも要らない。

```
public/
  index.html      本体
  favicon.svg
  images/         写真11点
```

## 手元で見る

```bash
python3 -m http.server 8420 --directory public
```

`.claude/launch.json` に同じ設定があるので、Claude Code からも起動できる。

## 公開

**Cloudflare Pages のプロジェクト `wakahoncafe`。** Git 連携はしていない。

**最初の公開はブラウザ経由。** Cloudflare Pages の静的アップロード（Drag and drop your files）に `public/` を放り込んだ。**コマンドを1つも打たずに公開できる**やり方で、ククデ会の初級でやっているのと同じ。

**2回目以降は wrangler を使ったかもしれない**（当時 wrangler を試していたため、記憶が確かでない）。**`.wrangler/cache/` ができていた**ので、少なくとも一度は `wrangler pages` 系のコマンドを動かしている。

いま更新するなら、どちらでもよい。

```bash
npx wrangler pages deploy public --project-name=wakahoncafe
```

`wrangler.jsonc` は置いていないので、プロジェクト名は毎回指定する。
