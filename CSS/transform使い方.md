# transformの使い方
## translateの使い方
- translateX()
```css
.translate:hover{
    transform: translateX(50px);
}
```
<img src="https://i.gyazo.com/d74d9b2a0e346651e577fd1e253b3e7b.gif">

----

- translateY()
```css
.translate:hover{
    transform: translateY(50px);
}
```
<img src="https://i.gyazo.com/4045a8e68886db5264c73bcd98b9ebc1.gif">

---

- translateZ()

translateZ()は、単体で設定しても、何の動きも実現してくれないので、遠近感を出すperspective()と一緒に使う。<br>
perspectiveを設定すれば、Zの値を0と考え、その時点でユーザーがどの位置にいるかを想定した値がpx数となる。<br>
perspective(500px)とすれば、ユーザーが500px時点の距離にいることを想定し、translateZ()の値を動かす。<br>
例えば、perspective(500px)で、translateZ(10px)と書けば、非常に細かな動きになり、逆にtranslateZ(1000px)と書けば、視界を飛び越えた動きをする。<br>
```css
.translate:hover{
    transform: perspective(500px) translateZ(100px);
}
```
<img src="https://i.gyazo.com/4bf08e06f2e9bf3beb3636c437d33fd7.gif">

---

- translate3d()
```css
.translate:hover{
    transform: perspective(400px) translate3d(30px, 30px, 30px);
}
```
<img src="https://i.gyazo.com/e9aed5d839218451dc71b55ce181669c.gif">

---

## rotateの使い方
「rotate」は、要素の回転を表現する値。これも同様にX軸、Y軸、Z軸のそれぞれの設定、あるいは、一括での設定が可能。<br>
以下は、rotate(20deg)で一括で指定している。「deg」とは「degree」で「度」を意味する。
- rotate()
```css
.translate:hover{
    transform: rotate(20deg);
}
```
<img src="https://i.gyazo.com/4682a6462041304c2b86102618d74170.gif">

---

- rotateX()
```css
.translate:hover{
    transform: rotateX(360deg);
}
```
<img src="https://i.gyazo.com/a00e70b1d221a6a20823e63283fe20c0.gif">

---

- rotateY()
```css
.translate:hover{
    transform: rotateY(360deg);
}
```
<img src="https://i.gyazo.com/c15147e0b279914e413d5482712e839e.gif">

---

- rotateZ()
```css
.translate:hover{
    transform: rotateZ(360deg);
}
```
<img src="https://i.gyazo.com/e7946917598bf4851458ecb1f2fae094.gif">

---

- rotate3d()
```css
.translate:hover{
    transform: rotate3d(10,10,10,360deg);
}
```
<img src="https://i.gyazo.com/425299d1dd2a50c5ec3666fc320c96f6.gif">

---

## scaleの使い方
scaleは、要素の拡大と縮小を実現できる。
- scale()

scale()では、scale(X軸の数値、Y軸の数値)を指定できる。2次元で縦と横に要素が拡大と縮小する。<br>
値には、「px」などの単位を設定する必要はない。「1.5」と書けば、「要素の1.5倍」、「0.5」と書けば、「要素の0.5倍」となる。また、「- 値」を設定すれば、縮小効果が得られる。
```css
.translate:hover{
    transform: scale(1.2, 1.2);
}
```
<img src="https://i.gyazo.com/0891a0f38e184d0f7fc5207098abe91e.gif">

---

- scaleX()
```css
.translate:hover{
    transform: scaleX(1.2);
}
```
<img src="https://i.gyazo.com/462466c60d766b0907540488d543597a.gif">

---

- scaleY()
```css
.translate:hover{
    transform: scaleY(1.2);
}
```
<img src="https://i.gyazo.com/b01ca320e50d706a317d800786bce3c0.gif">

---

- scaleZ()

scaleZ()は、Z軸方向に要素を動かすが、設定しても表向き変化を表現できない。scaleZ()を確認するには、3D効果を表現するようなその他の値と一緒に使う必要がある。<br>
わかりやすいようにscale(10)を設定する。
```css
.translate:hover{
   transform: perspective(400px) scaleZ(10) rotateX(45deg);
}
```
<img src="https://i.gyazo.com/e20b014d1b7cf8b6da5ec204a7bb6721.gif">

---

- scale3d()

scale3d()は、X軸、Y軸、Z軸を一括で指定できる。これもscaleZと同様に3D効果を表現する値と一緒に使わないと機能しない。
```css
.translate:hover{
   transform: perspective(400px) scale(1.5, 1.5,10) rotateX(45deg);
}
```
<img src="https://i.gyazo.com/1d83fed49adfe23136835aab18880f1c.gif">
          
 ---
 
## skewの使い方
skew関数は、要素の形を歪ませる、いわゆる傾斜効果を出すことができるが、他の関数と異なり、X軸とY軸での設定しかできないことが特徴。<br>
また、同様に注意したいことは、値を設定する際は、傾斜の角度(deg)で設定する。
- skew()
```css
.translate:hover{
   transform: skew(30deg, 30deg);
}
```
<img src="https://i.gyazo.com/b635b4855af116813a89823f77ec50fe.gif">

---

- skewX()
```css
.translate:hover{
    transform: skewX(30deg);
}
```
<img src="https://i.gyazo.com/7874288e36103ab5456aeba90c1a3fa4.gif">

---

- skewY()
```
.translate:hover{
    transform: skewY(30deg);
}
```
<img src="https://i.gyazo.com/9a91f6df939642e2ab87bb5c1ecdafcc.gif">

---

## transform-originの使い方
「transform-origin」は、変化の起点(原点)を設定するプロパティ。この起点の設定は、幾つかの設定方法がある。<br>
「絶対指定(px)」や「相対指定(%)」と「位置指定(top, center等)」。このミックス指定は上手く挙動しないので、統一して設定する。<br>
初期値は、要素の中心で「center center」か「50% 50%」となっている。
<img src="https://creive.me/wp-content/uploads/2018/11/d1db8e83a1baeb8c19d0124ed613e501.png">
