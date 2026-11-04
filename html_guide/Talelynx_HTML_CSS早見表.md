# Talelynx 作品紹介ページ HTML・CSS 早見表

2026年11月4日時点。デスクトップとiPhoneで実際に表示して確認した結果をまとめています（Androidは未確認）。

---

# 1. 基本のルール

- 文字数の上限は、全角・半角・改行を合計して20,000字です。
- CSSは、タグの `style="..."` に書くインライン指定だけが使えます。`<style>` タグ、`class`、外部CSSは使えません。
- 編集しやすくするため、タグごとに改行して書きます。行頭のインデント（空白）は不要です。
- 文章の途中で改行したいときは `<br>` を使います。ソース上の改行は、表示に反映されません。
- 画像は `{{img:画像名}}` で入れます。
- 文字の標準サイズは14px、行間は自動で1.35倍になります。

---

# 2. 使えるHTMLタグ

## 文章・見出し
- `<div>` `<p>` `<span>`
- `<h1>` `<h2>` `<h3>` `<h4>` `<h5>` `<h6>`
- `<br>`（改行）
- `<hr>`（区切り線）

## 文字の装飾
- `<b>` `<strong>`（太字）
- `<i>` `<em>`（斜体）
- `<u>`（下線）
- `<del>` `<s>`（打ち消し線）

## リンク・リスト・引用
- `<a>`（リンク。`href` と `target="_blank"` が使えます）
- `<ul>` `<ol>` `<li>`（箇条書き）
- `<blockquote>`（引用）

## そのほか
- `<details>` `<summary>`（折りたたみ。入れ子もできます）
- `<pre>` `<code>`（整形済みテキスト、コード）
- `<table>` `<thead>` `<tbody>` `<tr>` `<th>` `<td>`（表）

使えないタグの例：`<img>`（画像は `{{img:画像名}}` を使います）、`<iframe>`、`<script>`、`<style>`、`<button>`、`<input>`

---

# 3. 使えるCSS

## 文字
- `font-size`：px、%、em、rem、large などの単語、calc()
- `font-weight`：100〜900、bold
- `font-family`：serif、sans-serif、monospace、システムフォント名
- `letter-spacing`（字間）
- `word-spacing`（英単語の間隔）
- `line-height`（行間）
- `text-align`：left、center、right、justify
- `text-shadow`：複数指定もできます（グロー、フチ取り）
- `color`：#rgb、#rrggbb、8桁hex、rgba()、hsl()、色名

## 余白・サイズ
- `margin`、`padding`：一括指定で書きます。`margin:0px auto;` で中央寄せもできます
- 負のmarginは一括指定のみ：`margin:-8px 0px;`
- `width`、`height`、`max-width`、`min-width`、`min-height`
- `box-sizing:border-box`
- `overflow`：hidden と auto

## 枠線・角丸・影
- `border`：solid、dashed、dotted、double、groove、ridge、inset、outset
- `border-width`、`border-style`、`border-color`：4つの値をまとめて指定できます
- `border-radius`：一括指定。50%、999px、4つの値、`30px / 50%` もできます
- `box-shadow`：外側・inset・spread・半透明、カンマ区切りの複数指定もできます

## 背景
- `background`、`background-color`、`background-image`
- グラデーション：`linear-gradient`、`radial-gradient`、`conic-gradient`、`repeating-linear-gradient`、`repeating-radial-gradient`、`repeating-conic-gradient`
- グラデーションをカンマで複数重ねることもできます
- 背景の位置・サイズは一括指定の中に書きます。例：`background:linear-gradient(#cc0066,#cc0066) bottom/100% 3px no-repeat;`

## レイアウト
- `display`：block、inline、inline-block、none、table、table-row、table-cell、flex、inline-flex
- flex（横並びのみ）：`justify-content`、`align-items`、`flex-wrap`、`flex`、`flex-shrink`、`gap`、`margin-left:auto`
- table-cell の中での縦位置：`vertical-align:middle`

## 効果
- `backdrop-filter`：blur、saturate、brightness、contrast、hue-rotate（すりガラス風にできます）
- `cursor:pointer`（パソコンのみ意味があります）

## タグごとに使えること
- 見出し（h1〜h6）：サイズ、色、余白、背景、字間などを自由に変えられます
- 表：枠線、余白、背景、文字寄せ、`border-collapse:collapse`
- 折りたたみ（details）：背景、余白、角丸、色、太字、最初から開いておく `open` 指定
- リンク：色、`display:inline-block`、余白、角丸、背景グラデ

---

# 4. 使えないCSSと、代わりの方法

## 文字まわり
- 下線・打ち消し線（`text-decoration`）は使えません。`<u>`、`<del>`、`<s>` タグを使います。
- 斜体（`font-style`）は使えません。`<i>`、`<em>` タグを使います。
- 文字の半透明（`opacity`）は使えません。`color:rgba(0,0,0,0.5);` のように色で薄くします。
- 縦書き、字下げ（`text-indent`）、大文字化、折り返しの制御（`white-space` など）、「…」で省略する指定は使えません。
- 筆記体風のフォント（cursive、fantasy）、Google Fonts（iPhoneのみ）は使えません。
- グラデーションの文字、文字の縁取り（`-webkit-text-stroke`）は使えません。フチ取りは `text-shadow` を4方向に重ねます。

## 枠線・背景
- 一辺だけの枠線（`border-bottom` など）は使えません。代わりの方法は、次の「5. 線の作り方」を見てください。
- 辺ごとの個別指定（`border-top-color`、`border-left-width` など）は使えません。
- 角ごとの個別指定（`border-top-left-radius`）は使えません。`border-radius` の一括指定で書きます。
- 枠の外側の線（`outline`）は使えません。`box-shadow:0px 0px 0px 3px 色;` で代用します。
- 背景画像（`url()`）は、どの書き方でも使えません。
- `background-size` や `background-position` などの個別指定は使えません。一括指定の中に書きます。
- 要素全体の半透明（`opacity`）、`filter`、`mix-blend-mode` は使えません。
- `clip-path`、`mask`、`aspect-ratio` は使えません。

## 配置・変形
- `position`（relative、absolute、fixed、sticky）と `z-index` は使えません。
- `transform`、`rotate`、`scale`、`zoom` は使えません。
- `float`、`display:grid` は使えません。
- flex の `row-reverse` と `order`、縦並び（`flex-direction:column`）は使えません。
- `overflow` の scroll と横スクロールは使えません。
- ホバー（`:hover`）、`transition`、`animation` は使えません。

## リスト・段組み
- 箇条書きの黒丸や番号の変更（`list-style` 系）は使えません。見た目にこだわるときは、`<div>` と「・」「◆」などの記号で作ります。
- 段組み（`columns`）は使えません。

---

# 5. 線の作り方

一辺だけの枠線が使えないので、次の方法で作ります。

## 横線
```
<div style="height:1px;background:#555555;width:100%;margin:24px 0px;"></div>
```

## 縦線
```
<div style="display:block;width:0;height:60px;border-left:1px solid #9fc762;margin:12px auto;"></div>
```

## 下線だけ
```
<div style="border-style:solid;border-color:#cc0066;border-width:0px 0px 2px 0px;">文字</div>
```

## 左線だけ
```
<div style="padding-left:12px;box-shadow:inset 4px 0px 0px 0px #cc0066;">文字</div>
```

## 上下だけ
```
<div style="border:2px solid #cc0066;border-left:none;border-right:none;">文字</div>
```

---

# 6. 画像の使い方

- 画像は `<div>{{img:画像名}}</div>` の形で書きます。画像そのものにはCSSが効かないので、囲むdivに指定します。
- 囲むdivに使えるのは、`width`、`max-width`、`margin:0px auto;`（中央寄せ）、`border-radius`、`overflow:hidden`、`box-shadow` です。
- 画像を囲むdivには、上下に約8pxの余白が自動で付きます（左右には付きません）。角丸でぴったり収めたいときは、内側に入れ子のdivを置いて `margin:-8px 0px;` を付けると消えます。
- 画像には、標準で小さな角丸が付きます。
- 横に並べるときは、親のdivを `display:flex;gap:6px;` にして、それぞれに `flex:1` を付けます。
- `<img>` タグ、外部URLの画像、背景画像は使えません。

## 画像の上に文字を載せる
画像の直後に別のdivを置いて、負のmarginで重ねます。背景（グラデや半透明の色）を付けるときは、そのdivに `backdrop-filter:brightness(100%);` を付けて前面に出します。付けないと、背景が画像の裏に隠れます。

画像の下に約8pxの余白があるので、重ねるdivの負のmarginは、高さより8pxほど多く取ります（高さ70pxなら `margin:-78px 0px 0px 0px;`）。

---

# 7. 注意すること

## スマホ（iPhone）
- 読者の多くはスマホなので、iPhoneでの見え方を基準にします。
- Google Fonts は、iPhoneで反映されません。フォントは serif、sans-serif、monospace、システムフォント名で指定します。
- `vw`、`vh`、`vmin` は使いません。デスクトップでは、作品ページの幅ではなくブラウザ全体の幅が基準になって、はみ出します。幅は `%` か `px` で指定します。

## ダークモード
- 背景色を指定しない要素は、暗い背景に明るい文字で表示されます。
- 背景色を付けた要素には、必ず `color`（文字色）も指定します。背景だけを明るくすると、文字が読めなくなります。

## 書き方
- `margin-top:-6px` のような個別の負のmarginは効きません。`margin:-6px 0px 0px 0px;` のように一括指定で書きます。
- リンク（`<a>`）の下線は消せません。
- 引用（`<blockquote>`）には、左端に灰色の線が自動で付きます。
- `var()`（CSS変数）は、自動で除去される可能性があるので使いません。
- ここに載っていない記述は、未確認です。使うときは、先にテスト用の作品ページで表示を確かめるのが安全です。
