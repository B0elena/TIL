### NavigationBarItems
上の方にTextやButtonなどのUI部品を配置したい時に使うモディファイア<br>
NavigationViewの中でUI部品に追加して使う
``` swift
// 右上に表示させたい時
Navigation {
  UI部品
    .navigationBarItems (trailing: UI部品)
}

// 左上に表示させたい時
Navigation {
  UI部品
    .navigationBarItems (leadling: UI部品)
}
```
