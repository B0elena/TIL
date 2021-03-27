### ForEach
UI部品を繰り返し生成する為のもの<br>
ListやVStackなど複数のUI部品を配置できるものの中に記述する
- 数値範囲を用いて複数繰り返す方法
``` swift
ForEach(数値範囲) { 変数 in
  UI部品
}

List {
  ForEach(0..<11) { num in
    Text("\(num): Hell,World!")  // リストの中に順番の数字（0~10）とHell,World!が表示される
  }
}
```

- 構造体の配列から要素を一つずつ取り出していく方法
インスタンスを特定する為のIDを持たせるプロトコル（Identifableプロトコル）を適応させる必要がある
``` swift
ForEach(構造体の配列) { 変数 in
  UI部品
}

struct Human: Identifable {  // <- Identifableを適応
  let id = UUID()  // UUIDは適当なidを作成する関数
  let name: String
}

struct ContentView: View {
  let humans = [
    Human(name: "田中"),
    Human(name: "鈴木"),
    Human(name: "佐藤")
  ]
  
  var body: some View {
    List {
      ForEach(humans) { human in
        Text("\(human.name)さん、こんにちは！")  // 構造体の配列から要素を一つずつ取り出して表示する
      }
    }
  }
}
```
