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
<img src="https://creive.me/wp-content/uploads/2018/11/ead92844305f54fe5533c69f03471b5c.png">
          
---

```css
background: linear-gradient(#FA709A 30%, #FBAB7E 60%, #F7CE68 100%);
```
0%から30%までを「#FA709A」で、31%から60%までを「#FA709A」から「#FBAB7E」へと変化させ、61%から100%までを「#FBAB7E」から「#F7CE68」へ変化させる指示。
<img src="https://creive.me/wp-content/uploads/2018/11/b9ad2c0acf311d47fa5a51e0d66ec799.png">

---

### 方向と角度(傾斜)の指定
#### 上下左右を起点にする場合
グラデーションの方向を設定する場合、位置指定を行うことで、これを実現できる。初期設定は、上から下へのグラデーションだが、この方向を変更したければ、「top」、「right」、「bottom」、「left」といった位置を示すキーワードを置く。その際、キーワードの前に「to」を置く。
```css
background: linear-gradient(to left, #FA709A, #FBAB7E, #F7CE68);
```
<img src="https://creive.me/wp-content/uploads/2018/11/f2d129b30518126cbd3b503e57df890a.png">

|意味|位置|
|-|-|
|上から下へ|to bottom|
|右から左へ|to left|
|下から上へ|to top|
|左から右へ|to right|

---

#### 傾斜角度を設定する場合
方向指定では傾斜もある。この場合、角度指定のdeg(degree)を用いる。
```css
background: linear-gradient(45deg, #FA709A, #FBAB7E, #F7CE68);
```
左下を始点としたい場合は、45degを設定する。
<img src="https://creive.me/wp-content/uploads/2018/11/755994d701271ff33b4fcb0fc45493c5.png">

---
```css
background: linear-gradient(135deg, #FA709A, #FBAB7E, #F7CE68);
```
左上を始点としたい場合は、135degを設定する。
<img src="https://creive.me/wp-content/uploads/2018/11/83c2d04a361716bc64cea8032e3c4997.png">

---

```css
background: linear-gradient(315deg, #FA709A, #FBAB7E, #F7CE68);
```
右下を始点としたい場合は、315deg(-45deg)を設定する。
<img src="https://creive.me/wp-content/uploads/2018/11/83c2d04a361716bc64cea8032e3c4997.png">

---

```css
background: linear-gradient(-135deg, #FA709A, #FBAB7E, #F7CE68);
```
右上を始点としたい場合は、-135degを設定する。
<img src="https://creive.me/wp-content/uploads/2018/11/90c70efd5d32b319722be05382b8fab3.png">
