# CSSのtransformの使い方を理解する
```
    transform: rotate();
    transform: scale();
    transform: translate();
    transform: skew();
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
```
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
```
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
```
.tranceform:hover {
    transform: scaleX(1.5)scaleY(2)scaleZ(-40);
}
```
- scale3d()
```
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
## 5. transform-originで原点を変更

# transformで3Dの遠近感を表現する使い方
## 1. perspectiveで遠近感を表現
## 2. perspective-originで投影位置を変更
## 3. transform-styleで子要素を立体的にする
