## グラデーションを実現する2つの代表的なbackgroundの値
|値|説明|
|-|-|
|linear-gradient()|直線的グラデーションを作成できる。|
|radial-gradient()|楕円系のグラデーションを作成できる。|

## linear-gradient()の使い方
### 基本
グラデーションを実現するには、backgroundプロパティに対して、「linear-gradient」を設定する。<br>
直線的なグラデーションを実現することができる。
```css
background: linear-gradient(#FBAB7E, #F7CE68);
```
<img src="https://creive.me/wp-content/uploads/2018/11/3e296a8a31238f72a8c73342f7261ae5.png">

---

```css
background: linear-gradient(#FBAB7E 50%, #F7CE68);
```
スタート地点から見て0〜50%は#F13F79で塗られ、51〜100%がグラデーションになるということ。
<img src="https://creive.me/wp-content/uploads/2018/11/a0fc8af6afb91fb14522f49d6331cda3.png">

---

### 複数の色指定
```css
background: linear-gradient(#FA709A, #FBAB7E, #F7CE68);
```
<img src="https://creive.me/wp-content/uploads/2018/11/ead92844305f54fe5533c69f03471b5c.png=>
          
---

```css
background: linear-gradient(#FA709A 30%, #FBAB7E 60%, #F7CE68 100%);
```
0%から30%までを「#FA709A」で、31%から60%までを「#FA709A」から「#FBAB7E」へと変化させ、61%から100%までを「#FBAB7E」から「#F7CE68」へ変化させる指示。
<img src="https://creive.me/wp-content/uploads/2018/11/b9ad2c0acf311d47fa5a51e0d66ec799.png">

---

### 方向と角度(傾斜)の指定
