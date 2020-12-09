# CSS設計とは
## 1  OOCSS(Object Oriented CSS)
オブジェクト思考に基づいて考案された設計思考

### 使用法
構造と見た目、コンテナと内容を分離してclassを定義し、それらを組み合わせてスタイルを定義する。<br>
ID、子孫セレクタはなるべく使わなずに、スタイルはclassで定義して組み合わせる。

### メリット
- 再利用性とメンテナンスがしやすい
- 共通化することでコード量が減る

### デメリット
- コードが複雑になる
- 共通化によってどこにどのスタイルが当たるのか、CSSの見通しは悪くなる事がある
- CSSファイルの切り分けが上手く出来ていなかったり、どのパーツが共通化猿ているのがわかるガイドがない場合、新しくプロジェクトに参加するメンバーは初めに時間をかけてコードを読み理解しないといけない


## 2  SMACSS(Scalable and Modular Architecture for CSS)
OOCSSのコンセプトを元に作られた設計思考

### 使用法
スタイルをベース、レイアウト、モジュール、ステート、テーマの5つに分解する

### ベース
要素そのものデフォルトスタイル
### レイアウト
ページをエリア事に分解（layout-,l-など接頭字をつける）
### モジュール
再利用可能なパーツ（mod-,m-などの接頭字はつけない）
### ステート（状態）
レイアウトやモジュールの特定の状態を示す（is-接頭字をつける）
### テーマ
サイトのルック＆フィールを定義（theme-接頭字をつける）

<img src="https://image.slidesharecdn.com/css17-180606135525/95/css-10-638.jpg?cb=1528293469">

### メリット
- 再利用性とメンテナンスがしやすい
- どのファイルをいじればいいのかわかりやすい

### デメリット
- 場所に依存するパーツが多すぎるサイトでは良いところをいかせられない


## 3  BEM（Element Modifier）

### 使用法
要素をBlock, Element, Modifierの3つに分け、命名規則を元にClass名を記述する<br>
「Block-Element__Modifier」のように「-」や「＿＿」で区切って記述する
### Block
Blockはどこでも置く事ができ、Blockの中にBlockを含めることも可能
### Element
Elementはブロックの構成要素<br>
必ず頭にBlock名がつき、重複しないclass名になるので、Element以下はパターンで命名できる
### Modifier
同じElementでも異なる装飾を設定する場合使用<br>
KeyとValueという名前を付けてわかるやすくできる

### BEMを使用する上での注意
- 大枠からBEMで書いていくとElementが多くなりすぎて1つのclassが長くなるので、なるべく使い回せるボタンから作成すると使いやすい
- BEMの重要なことは、ElementかModifierかといった役割を明確にすること

### メリット
- どんなスタイルかわかりやすい
- コードの再利用がしやすい

### デメリット
- BEMを知らない人と一緒に書くと破綻する
- 1つのclass名が長くなり見ずらくなる事がある

## 4  FLOCSS(Foundation Layout Object CSS)
OOCSS SMACSS BEMを元に考案された設計思考
### FLOCSSの決まりごと
- 「Foundation」、「Layout」、「Object」、「Component」、「project」、「utility」で分ける
- 命名規則はBEMを使う
- 接頭字は「l」-layout,「c」-component,「p」-project,「u」-utility

### Sassを使う事が望ましい
<img src="https://image.slidesharecdn.com/css17-180606135525/95/css-24-638.jpg?cb=1528293469">
