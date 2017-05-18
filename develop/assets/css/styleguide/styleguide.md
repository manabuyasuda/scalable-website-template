/*doc
---
name: 概要
document: Styleguide
---

スタイルガイドは[Aigis](https://pxgrid.github.io/aigis/docs/jp/)で生成されています。

スタイルガイドは`/develop/assets/css/`内の.scssファイルと`/develop/assets/css/styleguide/`内の.mdファイルから生成されます。  
例えば、このドキュメントは`/develop/assets/css/styleguide/styleguide.md`から生成されています。

スタイルガイドのトップページは`index.md`を編集します。

*/


/*doc
---
name: Category
document: Styleguide
---

CategoryはAtomic Designの分類方法で指定しています。デザインをコードに変換する粒度の基準にしてください。

- [Atoms](/styleguide/Category/Atoms)：Atoms（アトム）は機能的にこれ以上分割ができない最小の要素です。例えば、見出しやリスト、フォームラベルやボタンなどが該当します。
- [Molecules](/styleguide/Category/Molecules/)：Molecules（モルキュール）はAtomsなどを組み合わせた比較的シンプルなUIグループです。例えば、検索フォームはlabelとinput、buttonが組み合わさったMoleculesです。
- [Organisms](/styleguide/Category/Organisms/)：Organisms（オルガニズム）はAtomsやMolecules、または複数のMoleculesを組み合わせた比較的複雑なUIグループです。例えば、グローバルヘッダーはロゴとグローバルナビゲーション、検索フォームなどが組み合わさったOrganismsです。
- [Templates](/styleguide/Category/Templates/)：Templates（テンプレート）はページレベルのオブジェクトで、コンポーネント（Atoms・Molecules・Organisms）を配置してページの構成を整えます。
- [Pages](/styleguide/Category/Pages/)：Pages（ページ）はTemplatesの動的なバリエーションです。例えば、ログインしているか、カートに入っているかといった特定の状況や、実際の画像やテキストを入れたときにレイアウトが崩れることはないかなどを確認します。

詳しくは[CSSのドキュメント](/styleguide/document/CSS/index.html#CSS設計手法)を確認してください。

*/


/*doc
---
name: Tag
document: Styleguide
---

Tagは以下のような分類で指定しています。コンポーネントの洗い出しの分類に使用してください。

- [Global](/styleguide/tag/Global/)：ヘッダーやフッターのようなサイト全体で使われる要素やレイアウト
- [Navigation](/styleguide/tag/Navigation/)：メインナビゲーションやフッターのナビゲーション、ページネーションやパンくずリストなどのユーザーを誘導することが目的とする要素
- [Image](/styleguide/tag/Image/)：ロゴやメインビジュアル、アバターやサムネイルや背景画像などの画像
- [Icon](/styleguide/tag/Icon/)：用途やカテゴリーを端的に示す画像です。虫眼鏡、ソーシャルアイコン、矢印、ハンバーガーなどです。
- [Form](/styleguide/tag/Form/)：入力エリア、Selectメニュー、チェックボックス、ラジオボタンのような、ユーザーが操作するフォーム要素
- [Button](/styleguide/tag/Button/)：オンオフやページ遷移、表示や非表示といった操作の切り替えに使われる要素
- [Heading](/styleguide/tag/Heading/)：ページタイトルや見出し
- [Text](/styleguide/tag/Text/)：文章やラベルのようなテキスト要素
- [Link](/styleguide/tag/Link/)：テキストリンク
- [List](/styleguide/tag/List/)：順序付きや定義リストなどのHTMLで定義されているリスト要素や、一覧や表といった形式であらわされている要素
- [Block](/styleguide/tag/Block/)：見出しや画像、テキストなどが1つのまとめりになっているエリア
- [InteractiveComponent](/styleguide/tag/InteractiveComponent/)：アコーディオン、タブ、カルーセル、オフキャンバスのようなユーザーの操作で稼働する要素
- [Media](/styleguide/tag/Media/)：ビデオやオーディオのようなリッチメディア要素
- [ThirdPartyComponent](/styleguide/tag/ThirdPartyComponent/)：サイト製作者側がすべてをコントロールすることができないサービス
- [Advertising](/styleguide/tag/Advertising/)：広告
- [Messaging](/styleguide/tag/Messaging/)：警告メッセージ、エラーメッセージ、ローディング、ポップアップのようなユーザーに何らかのメッセージを伝える要素

*/


/*doc
---
name: All Colors
document: Styleguide
---

スタイルガイド内で取得された色が自動で一覧化されます。

*/


/*doc
---
name: Document
document: Styleguide
---

コーディングルールやガイドラインなどをドキュメント化します。MarkdownやHTMLで書くことができます。

*/
