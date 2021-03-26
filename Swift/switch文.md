条件分岐の文法
``` swift
switch 条件式 {
  case 値１:
    値１の処理
  case 値２:
    値２の処理
  default:
    それ以外の処理
}

var number = 290
switch number {
  case 10:
    print(10)
  case 30:
    print(30)
  efault:
    print("それ以外")
}

// if文だとこう書ける
if number == 10 {
  print(10)
} else if number == 30 {
  print(30)
} else {
  print("それ以外")
}
```
