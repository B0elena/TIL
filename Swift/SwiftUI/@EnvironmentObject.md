### EnvironmentObject
@ObservedObjectをそれぞれのViewで共通のプロパティを使えるようにしたもの<br>
インスタンスの基となったクラスで、@Publishedがついているプロパティだけ<br>
変更された時にViewが更新されるようにしたいプロパティには@Publishedをつける<br>
Appの中で.environmentObject(クラス名())と記述する必要がある
``` swift
@ObservedObject var 変数名 = クラス名()  // @ObservedObject

@EnvironmentObject var 変数名: クラス名  // @EnvironmentObject
```
