



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
