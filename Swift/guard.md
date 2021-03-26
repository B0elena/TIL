条件に一致しなかった時に処理を中断する文法<br>
ifを使うより可読性が上がる<br>
関数やクロージャーの中で使わないとreturnが記述できない為、その中で使う
``` swift
guard 条件 else {
  条件に一致しなかったときの処理
  return
}
条件が一致した時の処理

var age = 24
func Drink () {
  guard age >= 20 else {
    print("お酒が飲めない")
    return
  }
  print("お酒が飲める")
}
Drink()  // -> お酒が飲めない
```
