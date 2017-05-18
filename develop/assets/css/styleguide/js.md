/*doc
---
name: 概要
document: JS
---

JavaScriptはGulpで連結と圧縮の処理だけをしています。

*/

/*doc
---
name: ディレクトリ構成
document: JS
---

JavaScriptは3つ大きくわけられます。

1. jquery
2. common
3. module

JQueryは`test/assets/js/`にそのまま出力されます。  
commonはサイト全体で使われるものを保存します。  
moduleはECSSの考えをベースに使われる場所や状況ごとにディレクトリをわけて、さらにModuleごとにファイルをわけます。

```bash
js/
├── common/
│   ├── breakpoint.js
│   ├── debounce.js
│   ├── jquery.matchHeight-min.js
│   └── throttle.js
├── jquery-2.2.0.min.js
└── module/
```

ファイルはすべて、`test/assets/js/`に出力されます。


*/
