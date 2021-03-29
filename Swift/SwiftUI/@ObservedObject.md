### @ObservedObject
インスタンス版の@State<br>
@ObservedObjectが付いたインスタンスのプロパティ変更された時にViewを更新<br>
インスタンスの基となったクラスで、@Publishedがついているプロパティだけ<br>
基となるクラスにObservedObjectプロトコルをつける<br>
変更された時にViewが更新されるようにしたいプロパティには@Publishedをつける<br>
ObservableObjectプロトコルがついたクラスを使ってインスタンスを作る時には@ObservedObjectをつける<br>
@ObservedObjectは複数のViewで使う場合、それぞれ独立したプロパティが使われる<br>
View全てで共通のプロパティを使いたい場合は@EnvironmentObjectを使う
``` swift
class クラス名: ObservedObject {
  @Published プロパティ１
  @Published プロパティ２
}
@ObservedObject var 変数名 = クラス名()
```

#### 例
``` swift
// UserDateという名前のファイルに
import swiftUI

class UserData: ObservedObject {
  @Published var name: String
  @Published var age: Int
  
  init(name: String, age: Int) {
    self.name = name
    self.age = age
  }
}
```
``` swift
// ContentViewファイルに
import swiftUI

struct ContentView: View {
  @ObservedObject var userData = UserData(name: "鈴木", age: 20)
  
}
```
