# CSSのtransformの使い方を理解する
```css
.transform {
    transform: rotate();
    transform: scale();
    transform: translate();
    transform: skew();
}
```
- rotateは回転
- scaleは拡大縮小
- translateは移動
- skewは歪み

transformの関数を「transform:関数()」と指定して値を指定することで、それぞれのtransform関数が持つ変形処理を実現していくのがCSSのtransformの使い方。
CSSのtransformは種類が多いため関数のコントロール次第で何パターンにも変化する使い方ができる。
またCSSのtransformで要素を変形する種類には「2Dトランスフォーム」と「3Dトランスフォーム」がある。<br>
2Dトランスフォームの場合はXY軸の2方向の変形処理<br>
3Dトランスフォームの場合はXYZ軸の3方向の変形処理<br>
 
## 1. rotateで回転
transformプロパティに使用するrotate()は「回転の指定」ができる関数<br>
```css
セレクタ名 {
　transform:rotate(回転角度deg);
}
```
rotateの値を(10deg)と正数で指定した場合は時計回りで回転。<br>
rotateの値を(-10deg)と負数で指定した場合は反時計回りに回転。<br>
CSSのtransformのrotate関数には次の4つの軸を加えて指定する使い方もでき、それぞれの軸の方向に回転させることができる。
- rotateX()
- rotateY()
- rotateZ()
- rotate3d()

rotate3d()関数を使うことでXYZ軸の変化をまとめて指定することもできる。<br>
rotate3dの値はXYZの順番に指定し、degで回転角度を決めて変化させる使い方ができる。
```css
.tranceform:hover {
    transform: rotate3d(30, 20, 10, 360deg);
}
```

## 2. scaleで拡大縮小をする
CSSでtransformのscale関数は拡大縮小ができる。<br>
- scaleX()
- scaleY()
- scaleZ()

scaleZで指定する場合は親要素にperspectiveプロパティを指定して遠近感を作りを変形させる。<br>
Z軸の変化は、遠近感を与えるtransformのプロパティや関数を組み合わせた使い方をしないと動作しない。<br>
scale()関数はX軸、Y軸、Z軸の縮小と伸縮の値を繋げて指定する使い方もできる。
```css
.tranceform:hover {
    transform: scaleX(1.5)scaleY(2)scaleZ(-40);
}
```
- scale3d()
```css
.tranceform:hover {
    transform: scale3d(1, 5, 2);
}
```

## 3. translateで移動させる
translate関数は要素に移動の処理をして変化をつけることができる。<br>
XY軸2つの方向を繋げて指定する使い方もできる。<br>
``` css
.tranceform:hover {
    transform: translateX(100px)translateY(-50px);
}
```
translateでXYの値をまとめて指定もできる。
```css
.tranceform:hover {
    transform: translate(100px, -50px);
}
```
translateでXYZの値を繋げて指定
```css
.tranceform:hover {
    transform: translateX(100px)translateY(100px)translateZ(100px);
}
```
translateでXYZの値をまとめて指定
```css
.tranceform:hover {
    transform: translate3d(100px, 100px, 100px);
}
```

## 4. skewで歪ませる
transformに指定するskewは座標系を「歪ませる」変形処理ができる関数
- skewX
- skewY
- skew
```css
.tranceform:hover {
    transform: skew(20deg, 30deg);
}
```

## 5. transform-originで原点を変更
CSSでtransformを適用すると適用した要素は、transform-originの初期値で構成してる原点を元に変形する動作をする。<br>
しかしtransform-originの初期値で構成してる原点の位置は値を指定することで原点を変更することができる。<br>
CSSのtransform-originプロパティの初期値の原点は2Dと3Dの初期値がある。
### transform-origin初期値

- 2D

50% 50%<br>
原点の位置が要素中央にセット
- 3D

50% 50% 0<br>
原点の位置が要素中央にセット

値指定0% 100%で要素の左下の辺を原点にして回転する。<br>
transform-originの値で原点を変更する値指定にはpxや%、leftやtopで指定ができる。<br>
```css
 transform-origin: 0% 100%;
 transform-origin: left top;
```
# transformで3Dの遠近感を表現する使い方
## 1. perspectiveで遠近感を表現
CSSのtransformでZ軸方向が奥行きになるが、Z軸方向の変形をしたい場合は、perspectiveを使用して遠近感を表現する。<br>
perspectiveは「関数」と「プロパティ」の2つの使い方がある。<br>
perspectiveを関数として指定して遠近感を表現する場合と、プロパティとして指定し遠近感を表現する場合では使い方が違う。

transformのperspective関数は指定した要素のみで遠近感が表現できる。
```
関数の場合(指定した要素のみ)
transform: perspective(値);
```
例えば、ホバーする要素にperspective(500px)と指定して値を500pxにしたとする。<br>
そしてtranslateZ(-200px)も繋げて指定した使い方をすると、perspectiveの値の500px分の遠近感が表現されながら、translateZで奥の方向に200px分ホバーしながら要素が移動する。要素が沈み込む感じ。
```
.trance-3d:hover {
    transform: perspective(500)translateZ(-200px);
}
```
一方でperspectiveプロパティの場合は親要素に指定。<br>
perspectiveプロパティを親要素に指定することで、その子要素の操作をできる。
```
プロパティの場合(親要素で指定して子要素だけに適用)
perspective:500px;
```

## 2. perspective-originで投影位置を変更
perspective-originは遠近感を表現するCSSでperspectiveプロパティを指定して透視投影というのが適用されたときの投影の中心位置を変更することができる。<br>
- perspective-originの初期値

50% 50%

中心位置を、たとえばperspective-originの値に「0% 50%」に変更すると投影の位置は親要素の左辺から50%の位置に変更できる。という使い方ができる。<br>
pxや%そして「left center right top center bottom」のキーワードで指定できる。

## 3. transform-styleで子要素を立体的にする
CSSのtransform-styleプロパティで子要素を2Dで表示するか、3Dで表示するかを指定できる。<br>
使い方は3D表示させたい要素の親要素にtransform-styleプロパティを指定しpreserve-3d関数を指定。<br>
親要素にpreserve-3d;を指定しない場合は親要素の表面で処理する。<br>
transform-styleは指定できる値が2つある。<br>
1つはpreserve-3d<br>
preserve-3dを使うと3D表示。<br>
2つ目はpreserve-flat<br>
preserve-flatはtransform-styleの初期値で2次元の処理になる。<br>
なのでpreserve-3dを指定して親要素を突き抜けた子要素は、親要素でpreserve-flatに指定を変えるだけで、親要素を突き抜けない2D処理の回転に変更できる。
