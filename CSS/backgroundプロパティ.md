## backgroundとは
「background」は、設定することより、背景の色を変更したり、画像を表示したりできるCSSプロパティ。<br>
backgroundで色や画像を設定するメリットは、HTMLで要素として表示させ、「display」などを使って、要素を上や下に配置するよりも、より容易に効果的な見栄えを実現できる事。<br>
「background」は、設定することより、背景の色を変更したり、画像を表示したりできるCSSプロパティ。<br>backgroundで色や画像を設定するメリットは、HTMLで要素として表示させ、「display」などを使って、要素を上や下に配置するよりも、より容易に効果的な見栄えを実現できるからです。
「imageタグ」との違いは、「imageタグ」はインライン要素として検索エンジンも認識するが、「background」で表示した画像はデザインとして扱われる。従って、検索エンジンにも認識してほしい重要度の高い画像はhtmlで書いた方が良いが、それほど重要度が高くないものは「background」で画像を設定する方が良い。

## backgroundプロパティの種類と値
|backgroundの種類|値|説明|
|-|-|-|
|background-color|「rgba()」か「#fef4f4」など16進数の値が取れる。	rgba()の場合は、「rgba(255, 255, 128, 0.4);」のように書き、最後の数値は、「0 – 1」までの値をとり、透明度を変えることができる。|
|background-image|url(絶対パス)かurl(相対パス)を設定する。	画像の設定は一つの場合が一般的だが、2つ以上の設定は可能。-colorと-imageを同時に設定した場合、-imageの設定が上にくる。|
|background-size|「cover」、「contain」、「%」、「px」などが設定できる。「cover」は設定範囲全体に横幅を合わせて表示される。また、「contain」は縦横比を保った上で表示さる。この場合は設定幅に対して余白が生じるケースが出てくるので、使用する際は注意が必要。|
|background-position|この値は、「px」、「%」の指定の他に「center」などの指定が可能。	X軸とY軸の位置設定が可能。位置指定の場合で、X軸とY軸の両方を設定する場合は、background-position: center(X軸) top(Y軸);のように設定される。一つの値の場合は、Y軸は「center」とみなされる。初期設定は、左上(left top)。位置指定の場合は、「center、left、right、top、bottom」がとれる値。|
|background-repeat|値は「repeat」「repeat-X」「repeat-Y」「no-repeat」の4つをとることができる。初期値は、画像の「repeat」なので、基本的に画像は繰り返し表示される。それをストップさせるには「no-repeat」を設定する必要がある。画像1枚だけを表示させる場合は、「no-repeat」を設定する。|
|background-attachment|値は、「scroll」、「fixed」、「local」のうちどれか1つをとる。「-attachment」は、背景画像を固定したり、スクロールしたりといった機能を提供する。|
|background-origin|値は、「border-box」、「padding-box」、「content-box」の3つをとる。background-originは、背景画像や背景色の基準点を設定できる。基準点は左上で、その起点を要素の右上か、paddingの右上か、borderの右上かを指定できる。|
|background-clip|値は、「border-box」、「padding-box」、「content-box」、「text」の4つをとる。background-clipは、背景画像や背景色をどの範囲で塗るかというイメージを持つと良い。「content-box」は、背景画像(背景色)を要素内で納めて配置する。「padding-box」はpadding内で背景画像(背景色)を配置する。「border-box」はborderの外側まで範囲を広げて背景画像(背景色)を配置する。|
