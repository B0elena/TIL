### 範囲演算子
``` swift
a...b  // bを含む
a..<b  // bを含まない
```

### 基本形
``` swift
for XX in コレクション {
  処理
}
```
### 配列
``` swift
for XX in 配列 {
  処理
}

var arr = [10, 20, 30, 40]
for num in arr {
  print(num)　　// 配列が順番に出力される
}
// タプル型で書ける
for (i, num) in arr.enumerated() {
  print(i, num)  // インデックス番号と一緒に出力される
}
```

### 辞書
``` swift
for (キー, 値) in 辞書 {
  処理
}

var f = ["apple": 1, "banana": 3, "orange":20]
for (key, value) in f {
  print(key, value)  // 辞書型は順番を保証しないので、どの順番で出力されるかわからない
}
// これでもOKで、タプルで出力される
for dic in f {
  print(dic)  
}
```

### 集合
``` swift
for XX in 集合 {
  処理
}

var numSet: Set = [0, 1, 2, 3]
for i in numSet {
  print(i)  // // 集合は順番を保証しないので、どの順番で出力されるかわからない
}

```
