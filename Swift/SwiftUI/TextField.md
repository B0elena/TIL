文字を入力する為のUI部品<br>
入力された文字は@Stateのついた変数に格納される
```swift
TextField(プレースホルダー, text: $入力を格納する変数)
```

### onCommit
TextFieldを使っている状態でリターンキーを押した時に、何らかの処理をする
``` swift
TextField(プレースホルダー, text: $入力を格納する変数,
  onCommit: {
    何らかの処理
  })
```
