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
``` swift
// 配列
for XX in 配列 {
  処理
}

var arr = [10, 20, 30, 40]
for num in arr {
  print(num)　　// 配列が順番に出力される
}
// タプル型で書ける
for (i, num) in 配列 {
  print(i, num)  // インデックス番号と一緒に出力される
}
```
