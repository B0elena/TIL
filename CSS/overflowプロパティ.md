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
}```
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
}```
<img src="https://creive.me/wp-content/uploads/2019/02/09f2755755d9917fe91720f37819575d.png">
