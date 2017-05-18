/*doc
---
name: 概要
document: CSS
---

CSSは[Sass](http://sass-lang.com/)を使って生成しています。  
その他の機能としてPostCSSなどを使って、いくつかの処理をしています。

- autoprefixer：ベンダープレフィックスの付与
- clean-css：スペースの削除やコメントも含めた省略可能なコードの削除（最適化）

*/

/*doc
---
name: 命名規則
document: CSS
---

命名規則は[MindBEMding](https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/)をベースに、なるべく短くしたものを使っています。

```scss
[namespace]-[blockName]
[namespace]-[blockName]_[elementName]
[namespace]-[blockName]-[modifierName]
[namespace]-[blockName]_[elementName]-[modifierName]
```

以下のようなルールがあります。

- `namespace`、`blockName`、`elementName`、`modifierName`の4つで構成される
- `namespace`と`blockName`は必須
- `namespace`はすべて小文字
- `blockName`、`elementName`、`modifierName`はローワーキャメルケース
- `namespace`と`blockName`の間はハイフン1つで区切る（`-blockName`）
- `elementName`はアンダースコア1つで区切る（`_elementName`）
- `modifierName`はハイフン1つで区切る（`-modifierName`）

`namespace`には後述するAtomic Designのカテゴライズに沿って、以下のようにつけます。

- Atoms -> `.a-`
- Molecules -> `.m-`
- Organisms -> `.o-`
- Templates -> `.t-`
- Pages -> `.p-`

コンポーネント名には見た目に関する言葉をできるかぎり避けてください。そのコンポーネントの役割や、どういうときに使うのかをできるだけ名前に含めてください。

```scss
// Bad
.icon-arrow {}
.listBullet {}

// Good
.icon-linkMore {}
.listUnordered {}
```

見た目に関する名前にすることによるデメリットは以下のようなものがあります。

- どういうときに使うのかがデザイナーにしか判断ができない
- 見た目が大きく変わるときに大幅にHTMLの修正も必要になる
- どこで使われているかが判断できないので削除することができない

*/

/*doc
---
name: CSS設計手法
document: CSS
---

CSSは[Atomic Design](http://atomicdesign.bradfrost.com/)をベースにしています。

### ディレクトリ構造
`develop/assets/css`以下にあるアンダースコア付きの`.scss`ファイルが`common.scss`によってインポートされます。

```bash
css/
├── common.scss
├── base/
│   ├── function/
│   ├── mixin/
│   └── variable/
├── atoms/
├── molecules/
├── organisms/
├── templates/
├── pages/
└── styleguide/
```

### Base
Baseレイヤーには、function、mixin、変数といったSassの機能と、normalize.cssや要素セレクタのベーススタイルが指定されています。

### Atoms（アトム）
Atomsレイヤーには、最小単位のコンポーネントが定義されています。

- アイコン
- 見出し
- テキスト
- リスト
- リンク
- etc.

Atomsコンポーネントはサイト内で繰り返し利用されます。ベーススタイルはmixinとして抽象化しておきます。

### Molecules（モルキュール）
Moleculesレイヤーには、Atomsを組み合わせたようなブロック（画像やテキストなどがひとまとまりになったコンポーネント）です。Molecules内のすべての要素がAtomsで定義されている必要はありません。

使う場所や状況（コンテキスト）をできるだけ明確にしておきます。mixinによって抽象化されているAtomsはMolecules内でインクルードします。Molecules内のAtomsのスタイルはMoleculesが上書きすることを許容しています。

### Organisms（オルガニズム）
0rganismsレイヤーは、複数のAtomsやMoleculesを組み合わせたMoleculesよりも大きな区画です。

使う場所や状況（コンテキスト）をできるだけ明確にしておきます。Organisms内のAtomsとMoleculesのスタイルはOrganismsが上書きすることを許容しています。

### Templates（テンプレート）
Templatesレイヤーは、OrganismsやMoleculesやAtomsの最終的なレイアウトを決めるオブジェクトです。ワイヤーフレームのような大枠のレイアウトを担当します。

トップページと詳細ページのようにコンテキストごとにレイアウトを決めてもいいですし、サイトの設計の意図と合致していれば1カラムと2カラムのようなレイアウトパターンで分けてもかまいません。

- [Get an overview of page layouts used on HealthCare.gov | HealthCare.gov Styleguide](https://styleguide.healthcare.gov/design/page-layouts)
- [Layouts | Harmony Design System](http://harmony.intuit.com/app-frameworks/layouts/)

### Pages（ページ）
Pagesレイヤーは、Templatesの動的なバリエーションです。基本的には、ログインしているか、カートに入っているかといった特定の状況に対応するために使います。

### 外部ライブラリや外部フレームワーク
JQueryのプラグインや、外部のCSSフレームワークなどを使う場合もAtomic Designのカテゴライズに沿って保存します。  
外部ライブラリであるかはではなく、機能や役割を基準に考えます。

*/


/*doc
---
name: ファイル名とblock名
document: CSS
---

Atomsレイヤー以下の各レイヤー内のファイルはBEMのblockごとにファイルを分割します。  
該当するコンポーネントを探しやすくするために、1つのファイルには1つのblockだけを入れるようにします。

- `.a-button` -> `atoms/_button.scss`
- `.m-table` -> `molecules/_table.scss`

*/

/*doc
---
name: Sass
document: CSS
---

Sassには変数や、便利なmixinをいくつか用意しています。

### メディアクエリ
`base/mixin/_mq.scss`にはメディアクエリを一括管理するmixinが用意されています。

例えば引数にブレイクポイントのキーワードを渡すと、

```scss
.foo {
  @include mq(md) {
    display: block;
  }
}
```

メディアクエリが出力されます。

```scss
@media (min-width: 720px) {
  .foo {
    display: block;
  }
}
```

ブレイクポイントは`base/variable/_breakpoint.scss`で定義しています。`md`と`lg`はデフォルトで使用しているので、名前は変更しないでください。

```scss
$breakpoint-up: (
  'sm': '(min-width: 480px)',
  'md': '(min-width: 720px)',
  'lg': '(min-width: 1200px)',
  'xl': '(min-width: 1680px)',
) !default;
```

また、`mq()`のように引数を渡さない場合の初期値は`base/variable/_global.scss`の`$default-breakpoint`で定義されています。  
引数なしの`mq()`を使うと、`$default-breakpoint`で一括管理できるようになるので管理がしやすくなります。

*/

/*doc
---
name: アイコンフォント
document: CSS
---

アイコンは基本的にSVGを背景画像で表示しますが、背景画像でカバーできないスタイルの場合はアイコンフォントを使います。

`develop/assets/icon/`にSVGを保存すると自動でアイコンフォントとCSSが生成されます。生成されたアイコンフォントは`css/atoms/_icon.scss`に出力されます。  SVGのファイル名がアイコンフォントのクラス名などに使われます。

SVGのファイル名は使うコンポーネント名をベースにします。アイコンフォントを使いまわさないことで、デザイン変更に柔軟に対応できるようにします。

基本的にはこのように専用のクラスを指定します。

```jade
p More
  span.a-icon.a-icon-linkMore(aria-hidden="true")
```

mixinと変数でアイコンフォントのスタイルを呼び出すこともできるので活用してください。

```scss
.a-linkMore_icon:after {
  @include a-icon; // アイコンフォントのベーススタイル
  content: "#{$icon-linkMore}"; // アイコンフォントの種類を指定
  top: -0.1em;
  left: 0.25em;
  font-size: 0.8em;
}
```

生成したアイコンフォントは`/styleguide/icon.html`で確認できます。

*/
