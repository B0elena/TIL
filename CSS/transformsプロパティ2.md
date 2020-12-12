## ベンダープレフィクス
要素に動きをつける「transform」ですが、ブラウザによっては対応していないものがあり、「ベンダープレフィクス」というものを付ける場合がある。<br>
これをつける理由は、「人によっては見ているブラウザが違っていて、そのブラウザによっては見えない人もいる。」ということを知っておく必要がある。

| ブラウザ | つけるベンダープレフィクス | つけ方(例) |
|-|-|-|
| Google Chrome/Safari | -webkit- | -webkit-transform: rotate(10deg); |
| Firefox | -moz- | -moz-transform: rotate(10deg); |
| Internet Explore | -ms- | -ms-transform: rotate(10deg); |
| Opera | -o- | -o-transform: rotate(10deg); |

## transformで使えるプロパティ
transformには、4つの関数が用意されていて、それを設定することで要素に動きがつけられる。

| プロパティ名 | 説明 |	関数名 |	意味 | 使い方 |
|-|-|-|-|-|
|transform | 要素の移動、変形を表現する | translate(移動効果) | translate() | X軸とY軸方向の設定ができる |
|||| translateX() | X軸方向の移動を設定できる |
|||| translateY() | Y軸方向の移動を設定できる |
|||| translateZ() | Z軸方向の移動を設定できるが、単体ではZ軸方向の移動は実現しない |
|||| translate3d() | X軸、Y軸、Z軸の移動を一括で設定できる |
||| rotate(回転効果) | rotate() | X軸、Y軸の2つの回転を設定できる |
|||| rotateX() | X軸の回転を設定できる |
|||| rotateY() | Y軸の回転を設定できる |
|||| rotateZ() | Z軸の回転を設定できるが、単体ではZ軸方向の回転は実現しない |
|||| rotate3d() | X軸、Y軸、Z軸の回転を一括で設定できる |


