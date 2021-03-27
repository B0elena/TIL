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
``` swift

```
