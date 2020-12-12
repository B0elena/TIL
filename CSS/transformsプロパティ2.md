

## transformで使えるプロパティ
transformには、4つの関数が用意されていて、それを設定することで要素に動きがつけられる。

| プロパティ名 | 説明 |	関数名 |	意味 | 使い方 |
|-|-|-|-|-|
| transform | 要素の移動、変形を表現する | translate(移動効果) | translate() | X軸とY軸方向の設定ができる |
|-|-|-| translateX() | X軸方向の移動を設定できる |
|-|-|-| translateY() | Y軸方向の移動を設定できる |
|-|-|-| translateZ() | Z軸方向の移動を設定できるが、単体ではZ軸方向の移動は実現しない |
|-|-|-| translate3d() | X軸、Y軸、Z軸の移動を一括で設定できる |
|-|-| rotate(回転効果) | rotate() | X軸、Y軸の2つの回転を設定できる |
|-|-|-| rotateX() | X軸の回転を設定できる |
|-|-|-| rotateY() | Y軸の回転を設定できる |
|-|-|-| rotateZ() | Z軸の回転を設定できるが、単体ではZ軸方向の回転は実現しない |
|-|-|-| rotate3d() | X軸、Y軸、Z軸の回転を一括で設定できる |
|-|-| scale(伸縮効果) | scale() | X軸、Y軸の2つの拡大、縮小を設定できる |
|-|-|-| scaleX() | X軸の拡大、縮小を設定できる |
|-|-|-| scaleY() | Y軸の拡大、縮小を設定できる |
|-|-|-| scaleZ() | Z軸の拡大、縮小を設定できるが、単体ではZ軸方向の拡大、縮小は実現しない |
|-|-|-| scale3d() | X軸、Y軸、Z軸の拡大、縮小を一括で設定できる |
|-|-| skew(歪み効果) | skew() | X軸、Y軸の歪み(傾斜)を設定できる |
|-|-|-| skewX() | X軸の歪み(傾斜)を設定できる |
|-|-|-| skewY() | Y軸の歪み(傾斜)を設定できる |
| transform-origin | 要素を動かしたり、変形させる起点を設定できる |-|-|-|
| transform-style | 要素の子要素を3Dで配置するか、平面配置か2つ設定ができる |-|-|-|
| perspective | 3D配置された要素に遠近感を与える効果を出す |-|-|-|
| perspective-origin | 3D配置された要素のユーザーからの見え方を決める |-|-|-|

## transformの使い方
### translateの使い方
#### translateX()
```css
.translate:hover{
    transform: translateX(50px);
}
```
<img src="https://i.gyazo.com/d74d9b2a0e346651e577fd1e253b3e7b.gif">

#### translateY()
```css
.translate:hover{
    transform: translateY(50px);
}
```
<img src="https://i.gyazo.com/4045a8e68886db5264c73bcd98b9ebc1.gif">

#### translateZ()
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

#### translate3d()
```css
.translate:hover{
    transform: perspective(400px) translate3d(30px, 30px, 30px);
}
```
<img src="https://i.gyazo.com/e9aed5d839218451dc71b55ce181669c.gif">

### rotateの使い方
「rotate」は、要素の回転を表現する値。これも同様にX軸、Y軸、Z軸のそれぞれの設定、あるいは、一括での設定が可能。<br>
以下は、rotate(20deg)で一括で指定している。「deg」とは「degree」で「度」を意味する。
#### rotate()
```css
.translate:hover{
    transform: rotate(20deg);
}
```
<img src="https://i.gyazo.com/4682a6462041304c2b86102618d74170.gif">

#### rotateX()
```css
.translate:hover{
    transform: rotateX(360deg);
}
```
<img src="https://i.gyazo.com/a00e70b1d221a6a20823e63283fe20c0.gif">

#### rotateY()

```css
.translate:hover{
    transform: rotateY(360deg);
}
```
<img src="https://i.gyazo.com/c15147e0b279914e413d5482712e839e.gif">

#### rotateZ()
```css
.translate:hover{
    transform: rotateZ(360deg);
}
```
<img src="https://i.gyazo.com/e7946917598bf4851458ecb1f2fae094.gif">

#### rotate3d()
```css
.translate:hover{
    transform: rotate3d(10,10,10,360deg);
}
```
<img src="https://i.gyazo.com/425299d1dd2a50c5ec3666fc320c96f6.gif">

### scaleの使い方
