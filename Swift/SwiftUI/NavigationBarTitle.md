### NavigationBarTitle
タイトルを作るモディファイア<br>
モディファイアとはUI部品をカスタマイズする為のメソッド<br>
.~  というように記述する<br>
NavigationViewの中で「Text」や「Button」のようなUI部品に追加して使う
``` swift
Navigation {
  何らかのUI部品
    .navigationBarTitle(Text("タイトルとして表示したい文字列"))
}
```
