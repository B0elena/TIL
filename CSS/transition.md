### transitionの定義
時間によるプロパティの変化を表現する
### transitionを使用するケース
- ボタンのデザイン
- 画像のホバーエフェクト
- avbarのnavメニューのデザイン
- レスポンシブデザインにおけるnavbarの伸縮効果

# transitionの使い方
## transitionプロパティの説明
|transitionプロパティ|説明|
|transition-property|ここにプロパティを設定することで、そのプロパティに動きがつくようになる。プロパティは複数個設定が可能。「all」を設定すると、全てのプロパティに動きがつく。|
|transition-duration|「動き」の継続時間を設定する。動きの開始から終わりまで何秒かけるかを秒単位(s)かミリ秒単位(ms)で指定する。|
|transition-delay|これを設定することで遅れて動きが始る。動きが始まるまでの時間を設定する。これも秒単位(s)かミリ秒単位(ms)で指定する。|
|transition-timing-function|動きの速度の変化を設定できる。初期値はeaseというもで、これ以外にもlinear(一定速度の変化)、ease-in(最初ゆっくり、後にはやく変化)、ease-out(最初は速く、後にゆっくり変化)などがある。|

## 個別指定と一括指定
### 個別指定
```css
.sample{
transition-property: 対象プロパティ;
transition-duration:　変化の継続時間;
transition-delay: 遅れて始まる時間;
transition-timing-function: アニメーション効果;
}
```
### 一括指定
```
.sample{
transition: 対象プロパティ 変化の継続時間 遅れて始まる時間 アニメーション効果;
}
```

### transition-timing-functionの種類
|transition-timing-functionプロパティの値|説明|
|-|-|
|linear|同じ速度で直線的な動きを表現する。|
|ease-in|最初はゆっくり、最後は速い動きを表現する。|
|ease-out|最初は速く、最後はゆっくりとした動きを表現する。|
|ease|最初は動きがゆっくり、途中で速くなり、最後はまたゆっくり動く変化を表現する。|
|ease-in-out|easeを多少早めた動きを表現する。|
|cubic-bezier()|ベジェ曲線のような動きを表現する。|
