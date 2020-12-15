## overflowの基本的役割
overflowプロパティは、要素の大きさから内容がはみ出た場合、その部分の処理に使われるCSSプロパティ
値1が水平方向(横方向)に対して適用され、値2は垂直方向(縦方向)に対して適用される。<br>
値が一つしかない場合は、同じ値を設定したものとみなされ、縦横同じ効果となる。
```css
.セレクタ{
  overflow: 値1, 値2
}
```
### 基本的役割
overflowの役割は、基本となる役割がある。それは、要素内に収まらない内容の表示方法の指定。<br>
つまり、要素からはみ出してしまったものを、表示させても良いのか、要素内に完全に含めて表示させたいのか、など表示に関する設定で使うことが基本。

### 応用的役割
時々本来の目的から外れた使い方もされる。例えば、floatを解除するために使われることもある。<br>
clearfixやclearbothと同じ効果が出せる。そのため、overflowはfloat解除の手段として理解されるが本来の使い方とは異なる。

```html
<div class="container">
    <div class="wrapper">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
    </div>
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</div>
```

```css
.wrapper p{
    width: 30%;
    float: left;
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/31f5c39536d7677035c8756f92f6abbb.png">
この回り込みを阻止するために、overflowを使うことができる。親要素であるwrapperクラスに「overflow:hidden;」を設定する。<br>
ポイントは親要素であるwrapperにoverflowを設定したこと。これによって、親要素のwrapperの高さと幅が決まり、そこからはみ出ることを許さなくなる。

```css
.wrapper p{
    width: 30%;
    float: left;
}
.wrapper{
    overflow: hidden;
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/09f2755755d9917fe91720f37819575d.png">

## overflowの値の種類
|値|説明|
|-|-|
|visible|これが初期値。これは要素から内容がはみ出す。つまり、何もしないという処理をする。|
|scroll|これを設定すると、要素の縦横を固定し、スクロールバーが表示される。そこからはみ出る内容は、スクロールをすることで見ることができるようになっている。|
|hidden|これを設定すると、要素の範囲以外の部分が非表示となる。|
|auto|これを設定すると、要素からはみ出た部分の処理をブラウザに委ねることになる。普通はこれを設定すれば、スクロールバーが表示される。この点でscrollと同じ。従って、目的を持って設定するのであれば、scrollとした方が良い。|

## overflowの使い方
### visible
これは初期値で、overflowを設定しない場合はこの設定になる。つまり、要素の大きさをはみ出て表示させる。
```css
.wrapper p{
        border:solid 1px blue;
　　　　 height:80px;
    overflow: visible;
     
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/b0887ae18c46452da4d2a66dd38f2ebc.png">

### scroll
crollの値をとると、要素内にスクロールバーが表示され、要素のサイズを保ちつつ、スクロールによって内容を見ることができる。
```css
.wrapper p{
        border:solid 1px blue;
　　　　 height:80px;
    overflow: scroll;
     
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/a36e1b617426bba4ab59c90999e081e7.png">
以下のように設定(white-space: nowrap;)すれば、下にスクロールバーが表示される。
```css
.wrapper p{
        border:solid 1px blue;
　　　　 height:80px;
    overflow: scroll;
    white-space: nowrap;
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/efc2d486a6e21b8623f2d8ddb19c32c5.png">

### hidden
hiddenは設定した要素以外の表示を非表示にする機能。要素内に収まらない内容があれば、それを見えなくする。
```css
.wrapper p{
    border:solid 1px blue;
    width:100%;
    height:80px;
    overflow: hidden;
}
```

### auto
これは、ブラウザにその処理を委ねるが、基本的な結果は、scrollの場合と変わらない。
```css
.wrapper p{
        border:solid 1px blue;
　　　　 height:80px;
    overflow: auto;
     
}
```
<img src="https://creive.me/wp-content/uploads/2019/02/4b0117a4d308af9778d3e979de2f6231.png">


## overflow-xとoverflow-yの使い方
