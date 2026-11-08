# Talelynx 作品紹介ページ HTML・CSS 早見表(第2版)

第1版: 2026年11月4日。デスクトップとiPhoneで実際に表示して確認した結果(Androidは未確認)。
第2版: 2026年11月8日。公式の「紹介文デコレーションガイド(HTML・Markdown)」と突き合わせて、書き漏れていた項目を補いました。

見分け方:
- 【実機確認】: 第1版のテストで確かめた内容です。
- 【v2追加・公式記載】: 公式ガイドに書いてあり、まだ実機で確かめていない内容です。
- 【v2追加・食い違い】: 公式の記載と実機テストの結果が違う内容です。実機テストの結果を優先しています。

---

# 1. 基本のルール

- 紹介文は2種類あります。【v2追加・公式記載】
  - チャット紹介(共通): PCでもスマホでも表示されます。
  - スマートフォン用のチャット紹介: スマホだけ別の内容にできます。空欄なら共通のものが使われます。
  - どちらも、HTMLタグを含めて20,000字までです。
- 文字数の上限は、全角・半角・改行を合計して20,000字です。
- 入力欄の上に「テキスト長(推定)」が出ます。タグが長くなる凝ったデザインでは、これで実際の量を確認します。【v2追加・公式記載】
- CSSは、タグの `style="..."` に書くインライン指定だけが使えます。`<style>` タグ、`class`、外部CSSは使えません。
- 編集しやすくするため、タグごとに改行して書きます。行頭のインデント(空白)は不要です。
- 文章の途中で改行したいときは `<br>` を使います。ソース上の改行は、HTMLの中では表示に反映されません。
- 画像は `{{img:画像名}}` で入れます。
- 文字の標準サイズは14px、行間は自動で1.35倍になります。
- 入力欄の下にリアルタイムプレビューがあります。ライト/ダークの切り替えと、スマホ専用プレビューもあります。公開前に必ず両方で確かめます。【v2追加・公式記載】

---

# 2. 使えるHTMLタグ

## 文章・見出し
- `<div>` `<p>` `<span>`
- `<h1>` `<h2>` `<h3>` `<h4>` `<h5>` `<h6>`
- `<br>`(改行。`<br />` の書き方でも可)
- `<hr>`(区切り線)

## 文字の装飾
- `<b>` `<strong>`(太字)
- `<i>` `<em>`(斜体)
- `<u>`(下線)
- `<del>` `<s>`(打ち消し線)

## リンク・リスト・引用
- `<a>`(リンク。`href` と `target="_blank"` が使えます)
- `<ul>` `<ol>` `<li>`(箇条書き)
- `<blockquote>`(引用)

## そのほか
- `<details>` `<summary>`(折りたたみ。入れ子もできます)
- `<pre>` `<code>`(整形済みテキスト、コード)
- `<table>` `<thead>` `<tbody>` `<tr>` `<th>` `<td>`(表)

## 使えないタグ
- `<iframe>`、`<script>`、`<style>`、`<button>`、`<input>` は使えません。
- 上の一覧にないタグは、すべて取り除かれます。タグだけが消えて、中の文字は残ります。【v2追加・公式記載】
- `onclick` などのイベント属性と、`javascript:` のリンクは、安全のためすべてブロックされます。【v2追加・公式記載】

## `<img>` タグについて【v2追加・食い違い】
- 公式ガイドには「`<img src alt title style>` が使える(http/httpsのURLか、base64のみ)」と書かれています。
- しかし実機テストでは、`<img>` タグも外部URLの画像も表示されませんでした。
- そのため、画像は `{{img:画像名}}` だけを使います。

## リンクの注意【v2追加・公式記載】
- `href` に使えるのは、`http` / `https` / `mailto` / `tel` だけです。
- Markdownで書いたリンクは、自動で新しいタブで開きます。

---

# 3. 使えるCSS

## 文字
- `font-size`: px、%、em、rem、large などの単語、calc()
- `font-weight`: 100〜900、bold
- `font-family`: serif、sans-serif、monospace、システムフォント名
- `letter-spacing`(字間)
- `word-spacing`(英単語の間隔)
- `line-height`(行間)
- `text-align`: left、center、right、justify
- `text-shadow`: 複数指定もできます(グロー、フチ取り)
- `color`: #rgb、#rrggbb、8桁hex、rgba()、hsl()、色名

## 余白・サイズ
- `margin`、`padding`: 一括指定で書きます。`margin:0px auto;` で中央寄せもできます
- 負のmarginは一括指定のみ: `margin:-8px 0px;`
- `width`、`height`、`max-width`、`min-width`、`min-height`
- `box-sizing:border-box`
- `overflow`: hidden と auto

## 枠線・角丸・影
- `border`: solid、dashed、dotted、double、groove、ridge、inset、outset
- `border-width`、`border-style`、`border-color`: 4つの値をまとめて指定できます
- `border-radius`: 一括指定。50%、999px、4つの値、`30px / 50%` もできます
- `box-shadow`: 外側・inset・spread・半透明、カンマ区切りの複数指定もできます

## 背景
- `background`、`background-color`、`background-image`
- グラデーション: `linear-gradient`、`radial-gradient`、`conic-gradient`、`repeating-linear-gradient`、`repeating-radial-gradient`、`repeating-conic-gradient`
- グラデーションをカンマで複数重ねることもできます
- 背景の位置・サイズは一括指定の中に書きます。例: `background:linear-gradient(#cc0066,#cc0066) bottom/100% 3px no-repeat;`

## レイアウト
- `display`: block、inline、inline-block、none、table、table-row、table-cell、flex、inline-flex
- flex(横並びのみ): `justify-content`、`align-items`、`flex-wrap`、`flex`、`flex-shrink`、`gap`、`margin-left:auto`
- table-cell の中での縦位置: `vertical-align:middle`

## 効果
- `backdrop-filter`: blur、saturate、brightness、contrast、hue-rotate(すりガラス風にできます)
- `cursor:pointer`(パソコンのみ意味があります)

## タグごとに使えること
- 見出し(h1〜h6): サイズ、色、余白、背景、字間などを自由に変えられます
- 表: 枠線、余白、背景、文字寄せ、`border-collapse:collapse`
- 折りたたみ(details): 背景、余白、角丸、色、太字、最初から開いておく `open` 指定
- リンク: 色、`display:inline-block`、余白、角丸、背景グラデ

## 公式の許可リストについて【v2追加・公式記載】
- 公式ガイドには、使えるプロパティの一覧があります。実機テストでは、その一覧に載っていないもの(`flex-shrink`、`vertical-align`、`border-collapse` など)も使えました。
- つまり、公式の一覧は全部ではありません。実機で確かめたものは、このページの内容を優先します。

## 自動で取り除かれる指定【v2追加・公式記載】
- 許可されていないプロパティの指定は、まるごと消えます。
- 値の中に `url(...)`、`expression(...)`、`javascript:`、`@import`、`var(...)` が入っている指定は、まるごと消えます。
- 1つの値が300文字を超えると、その指定は消えます。何枚も重ねた長いグラデーションなどは、300文字に収まるか気をつけます。

---

# 4. 使えないCSSと、代わりの方法

## 文字まわり
- 下線・打ち消し線(`text-decoration`)は使えません。`<u>`、`<del>`、`<s>` タグを使います。
- 斜体(`font-style`)は使えません。`<i>`、`<em>` タグを使います。
- 文字の半透明(`opacity`)は使えません。`color:rgba(0,0,0,0.5);` のように色で薄くします。
- 縦書き、字下げ(`text-indent`)、大文字化、折り返しの制御(`white-space` など)、「…」で省略する指定は使えません。
- 筆記体風のフォント(cursive、fantasy)、Google Fonts(iPhoneのみ)は使えません。
- グラデーションの文字、文字の縁取り(`-webkit-text-stroke`)は使えません。フチ取りは `text-shadow` を4方向に重ねます。

## 枠線・背景
- 一辺だけの枠線(`border-bottom` など)は使えません。代わりの方法は、次の「5. 線の作り方」を見てください。
- 辺ごとの個別指定(`border-top-color`、`border-left-width` など)は使えません。
- 角ごとの個別指定(`border-top-left-radius`)は使えません。`border-radius` の一括指定で書きます。
- 枠の外側の線(`outline`)は使えません。`box-shadow:0px 0px 0px 3px 色;` で代用します。
- 背景画像(`url()`)は、どの書き方でも使えません。
- `background-size` や `background-position` などの個別指定は使えません。一括指定の中に書きます。
- 要素全体の半透明(`opacity`)、`filter`、`mix-blend-mode` は使えません。
- `clip-path`、`mask`、`aspect-ratio` は使えません。
- `object-fit` と `object-position` は使いません。【v2追加・食い違い】公式の許可リストには載っていますが、実機テストでは使えませんでした。

## 配置・変形
- `position`(relative、absolute、fixed、sticky)と `z-index` は使えません。
- `transform`、`rotate`、`scale`、`zoom` は使えません。
- `float`、`display:grid` は使えません。
- flex の `row-reverse` と `order`、縦並び(`flex-direction:column`)は使えません。
- `overflow` の scroll と横スクロールは使えません。
- ホバー(`:hover`)、`transition`、`animation` は使えません。

## リスト・段組み
- 箇条書きの黒丸や番号の変更(`list-style` 系)は使えません。見た目にこだわるときは、`<div>` と「・」「◆」などの記号で作ります。
- 段組み(`columns`)は使えません。

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
- 囲むdivに使えるのは、`width`、`max-width`、`margin:0px auto;`(中央寄せ)、`border-radius`、`overflow:hidden`、`box-shadow` です。
- 画像を囲むdivには、上下に約8pxの余白が自動で付きます(左右には付きません)。角丸でぴったり収めたいときは、内側に入れ子のdivを置いて `margin:-8px 0px;` を付けると消えます。
- 画像には、標準で小さな角丸が付きます。
- 横に並べるときは、親のdivを `display:flex;gap:6px;` にして、それぞれに `flex:1` を付けます。
- `<img>` タグ、外部URLの画像、背景画像は使えません。
- 画像の名前は、制作画面のステップ5で登録した名前と1文字も違わないように書きます。名前の欄にある「名前コピー」ボタンを使うと間違えません。【v2追加・公式記載】
- 外部URLの画像より、ギャラリーに登録して `{{img:画像名}}` で呼ぶほうが、リンク切れの心配がなく安全です。【v2追加・公式記載】

## 画像の上に文字を載せる
画像の直後に別のdivを置いて、負のmarginで重ねます。背景(グラデや半透明の色)を付けるときは、そのdivに `backdrop-filter:brightness(100%);` を付けて前面に出します。付けないと、背景が画像の裏に隠れます。

画像の下に約8pxの余白があるので、重ねるdivの負のmarginは、高さより8pxほど多く取ります(高さ70pxなら `margin:-78px 0px 0px 0px;`)。

---

# 7. Markdownの使い方【v2追加・公式記載】

紹介文では、HTMLのほかにMarkdown(GFM準拠)も自動で変換されます。第1版にはこの項目がありませんでした。実機での確認はまだです。

## 使える書き方
- `# 見出し`(`#` が1〜6個。6段階)
- `**太字**` または `__太字__`
- `*斜体*` または `_斜体_`
- `~~取り消し線~~`
- 行頭の `- ` で箇条書き
- 行頭の `1. ` で番号付きリスト
- 行頭の `> ` で引用
- `| 列 | 列 |` の形式で表
- `---` だけの行で区切り線
- `[テキスト](URL)` でリンク(新しいタブで開く)
- `![説明](画像URL)` で外部画像(`<img>` と同じく、実機で表示されるかは未確認です)
- Markdownの文章は、改行がそのまま改行として表示されます(空行は不要)

## 知っておきたい仕様
- HTMLとMarkdownは、同じ紹介文の中で自由に混ぜて書けます。以前あった「HTMLタグが1つでもあるとMarkdownが無効になる」制限は、なくなっています。
- 行頭に4つ以上スペースを入れても、コードブロックにはなりません。コードブロックを使いたいときは、半角バッククォート3つで囲みます。
- 文章の次の行に `---` や `===` を置いても、見出しにはなりません。`---` は必ず区切り線になります。見出しは `#` で書きます。
- 第1版の「ソース上の改行は反映されない」は、HTMLの中の話です。Markdownの文章では改行が反映されます。混ぜて書くときは、プレビューで確かめます。

---

# 8. 紹介文だけで使える特別な書き方【v2追加・公式記載】

- `{user}` または `{{user}}`: 紹介文を見ている人のペルソナ名に置き換わります。例:「{user}、あなたを待っていました」
- `{{img:画像名}}` と見た目が似ているので、名前の置き換えには波かっこ1つの `{user}` を使うと間違えにくいです。
- 実機での確認はまだです。

---

# 9. スマホ用の紹介文のコツ【v2追加・公式記載】

- スマホ用は、共通の紹介文とは別に、20,000字まで書けます。
- 短い段落と、縦に並べるレイアウトが向いています。
- 専用のスマホ用プレビューで確かめます。
- 空欄にすると、共通の紹介文がそのまま使われます。

---

# 10. 注意すること

## スマホ(iPhone)
- 読者の多くはスマホなので、iPhoneでの見え方を基準にします。
- Google Fonts は、iPhoneで反映されません。フォントは serif、sans-serif、monospace、システムフォント名で指定します。
- `vw`、`vh`、`vmin` は使いません。デスクトップでは、作品ページの幅ではなくブラウザ全体の幅が基準になって、はみ出します。幅は `%` か `px` で指定します。

## ダークモード
- 背景色を指定しない要素は、暗い背景に明るい文字で表示されます。
- 背景色を付けた要素には、必ず `color`(文字色)も指定します。背景だけを明るくすると、文字が読めなくなります。

## 書き方
- `margin-top:-6px` のような個別の負のmarginは効きません。`margin:-6px 0px 0px 0px;` のように一括指定で書きます。
- リンク(`<a>`)の下線は消せません。
- 引用(`<blockquote>`)には、左端に灰色の線が自動で付きます。
- `var()`(CSS変数)は使いません。公式ガイドでも、`var(...)` を含む指定は必ず取り除かれると書かれています。
- ここに載っていない記述は、未確認です。使うときは、先にテスト用の作品ページで表示を確かめるのが安全です。

## 確認のしかた【v2追加・公式記載】
- 貼り付けたあとは、必ず入力欄の下のプレビューを見ます。
- プレビューで消えたり崩れたりする部分は、許可されていないタグや属性が使われているしるしです。その部分だけを許可タグで書き直します。
- ライトとダークの両方、共通とスマホ用の両方で確かめます。

## AIに紹介文を作らせるときの伝え方【v2追加・公式記載】
公式ガイドも、ChatGPTなどのAIに作らせることを勧めています。ただ、AIは許可されていないタグを使いがちなので、条件を一緒に伝えます。伝える内容の例です。
- 使えるタグを列挙する
- `script`、`iframe`、`style` タグ、イベント属性、`class`、`position`、`animation` は使わせない
- 使えるCSSの範囲を伝える
- 改行は `<br>` で書かせる
この早見表と対になっている「AI向け仕様書(第2版)」を渡すと、これらがまとめて伝わります。
