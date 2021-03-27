### Button
クリックした時に何らかの処理を行うUI部品のこと<br>
ボタンが押された時の処理は、関数かクロージャーを使う<br>
ボタンの見た目には、TextなどのUI部品を使う

``` swift
Button(action: ボタンが押された時の処理) {
  ボタンの見た目
}

Button(action: Report) {
  Text("ボタンを押してください")
}

func Report() {
  print("ボタンが押されました")
]
```
