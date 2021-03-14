## val と var の違い
- val：読み込み専用（Getterのみ）
- var：書き換え可能（Getter,Setter）
 
### 定数（const）
constを付ける。アンダースコア区切りの大文字で記述。
```kotlin
const val MAX_COUNT = 8
```


## Null-safety
### null-type と non-null-type
NULLチェックしてないコードはコンパイル段階でエラー。<br>
できるだけnon-null-typeを使う。<br>
必要な場合のみnull-type。

``` kotlin
non-null-type
var a: String = "abc"   // non-null type
a = null                // 代入できない。エラー
val l = a.length        // ok
```
``` kotlin
null-type（？をつける）
var a: String? = "abc"  // null type
a = null                // null代入できる
val l = a.length        // nullチェックしてない。エラー
```

### nullなら実行しない安全呼び出し
``` kotlin
val thread: Thread? = null
thread?.start()
```

### nullの代替値
nullじゃなかったら設定、のような場合<br>
エルビス演算子?:を使って完結にできる。
```kotlin
textView.setText(name?: "no name");
```
```kotlin
// エルビス演算子おまけ。dataがnullになるならreturnする
val data = Hoge.getData ?: return
```

### 非null表明
null-typeをnon-null-typeに強制変換します。
```kotlin
fun length(str: String?) : Int = str!!.length

〜中略〜

length("hoge") // ４を返す
length(null)   // NullPointerExcelption
```
どうしてもな場合はrequireNotNull関数でメッセージを残す。
```kotlin
val a: Int? = null
val b: Int? = requireNotNull(a) {"ぬるぽ"}  // 第二引数の文字列は任意
```

## 文字列 string
ダブルクォーテーションで囲うのは一緒<br>
文字列中に変数を埋め込む（String Template）場合は$マークを付けて、｛｝で囲う
``` kotlin
val name: String = "ssuzaki"
println("${name}")
```
型を類推できる場合は更に｛｝も省略可能
``` kotlin
println("$name")
```

### raw string
改行を含めて書いた通りの文字列を表現する場合はダブルクォーテーションを３つで囲う。<br>
行頭の|は目印の記号で、それが結果に含まれないようにtrimMarginしている。

``` kotlin
fun main(args: Array<String>) {
    val text = """
        |むかしむかし
        |あるところに
        |じーさんばーさんが
        """.trimMargin()

    println("$text")
}
```

## 関数 function
``` kotlin
// ４パターン
fun sum(a: Int, b: Int): Int{
    return a + b
}

fun sum(a: Int, b: Int) = a + b

fun sum(a: Int, b: Int): Unit {  // 何も返さないよ
    print(a + b)
}

fun sum(a: Int, b: Int) {  // Unitは省略できる
    print(a + b)
}
```

### デフォルト引数
``` kotlin
open class HogeView : ImageView {
    constructor(context: Context, attrs: AttributeSet? = null, defStyleAttr: Int = 0)
    : super(context, attrs, defStyleAttr) {
    }
}
```

### 名前付き引数
引数名を使って関数呼び出しすると似たような関数を減らせる。
```kotlin
fun addData(name: String, age: Int = 0): String {
    return "$name + $age"
}

val result1 = addData(age = 20, name = "hoge")
val result2 = addData("hoge", age = 30)
val result3 = addData("hoge")
```

### 可変長引数
可変長にしたい引数をvarargで修飾すると配列として扱われる。<br>
１つの関数で１つまでしか定義できない。
``` kotlin
fun main(args: Array<String>) {
    println( sum(1,2,3) )
    println( sum(*intArrayOf(1,2,3)) )  // 配列を渡す場合は*が必要
}

fun sum(vararg items: Int): Int {
    var total = 0
    for(item in items) {
        total += item
    }
    return total
}
```

### 再帰
``` kotlin
// これが
fun sum(num: Int): Int {
    if (num != 0)
        return num + sum(num - 1)
    else
        return num
}

// こう書ける。tailrecで修飾すると再帰が最適化されます。
tailrec fun sum(num: Int, total:Int = 0) : Int
    = if(num != 0) sum(num - 1, total + num) else total
```

### ローカル関数 local function
関数内関数です。スコープがその関数内に限定されます。
```kotlin
fun main(args: Array<String>) {
    println( unko(true) )
}

fun unko(isHoge: Boolean): String {
    fun hoge(): String = "hoge"
    if(isHoge) return hoge() else return "unko"
}
```

### 値を返さない関数
javaでいうvoid？　Unit型の関数は値を返さなくてもいいそうです
```kotlin
class Hoge() {
    private var cnt = 0
    fun count(): Unit {
        cnt ++
    }    
    fun count2() {  // Unitは省略するのが普通ぽい
        cnt ++
    }
}
```

### 関数オブジェクト
関数名の頭に::を付けると関数オブジェクトが取得でき、関数として呼び出せる。
``` kotlin
fun main(args: Array<String>) {
    // 型を類推
    val function = ::unko
    println( function() )

    // 型を明示
    val function2: () -> String = ::unko
    println( function2() )
}

fun unko(): String {
    return "unko"
}
```

### ラムダ式
関数を定義せず、直接関数オブジェクトを生成します。
``` kotlin
fun main(args: Array<String>) {
    val square: (Int) -> Int = { i: Int -> i * i }  // ラムダ式
    val square2: (Int) -> Int = { i -> i * i }      // 型推論
    val square3 = { i:Int -> i * i }                // 型推論
    val square4: (Int) -> Int = { it * it }         // 引数が１つの場合はitの名で変数が使える
}
```

## 制御文 Control Flow
### if
ifは式で値を返します。なので三項演算子はありません。
``` kotlin
// 普通に書けます。
var max = a
if (a < b)
    max = b

// elseも書けます。
var max: Int
if (a > b)
    max = a
else
    max = b

// 式
val max = if (a > b) a else b

// 分岐はブロックにできます。ブロックの最後の式が値になります。
val max = if (a > b) {
    print("Choose a")
    a
} else {
    print("Choose b")
    b
}
```

### when
引数ありなしどっちでもいける。分岐条件に定数じゃないものも書ける。

- when(引数あり) { ... }
- when {...} 引数なし
- ==, ||, && も使える

ので、if-else,else,else...よりも見やすい。
``` kotlin
// 引数あり
fun cases(obj: Any) {
    when (obj) {
        1          -> println("One")
        2,3 ->     -> println("Two or Three")
        in 4..9    -> println("Four to  Nine")
        "Hello"    -> println("Greeting")
        is Long    -> println("Long")
        !is String -> println("Not a string")
        else       -> println("Unknown")
    }
}

fun main(args: Array<String>) {
    cases(1)

    cases("Hello")

    val a: Long = 1;
    cases(a)   

    cases(2)

    cases("test")
}
```
結果
```
One
Greeting
Long
Not a string
Unknown
```
``` kotlin
// 引数なし版
when {
    hoge.isOld() -> println("old")
    hoge.isNew() -> println("new")
}
```

### for
``` kotlin
// くるくる
for (item in collection)
    print(item)

// ブロックくるくる
for (item: Int in ints) {
    // ...
}

// インデックスでくるくる
for (i in array.indices)
    print(array[i])

// インデックスと値でくるくる
for ((index, value) in array.withIndex()) {
    println("the element at $index is $value")
}

// 範囲でくるくる
for (i in 1..10) {
    println(hoge(i))
}

// downTo, step の指定
for (i in 100 downTo 1 step 2) {
    println(hoge(i))
}

// listがnullのケースも考慮したパターン１。listがnullだとforに入らない
for (i in list.orEmpty())  {
}

// listがnullのケースも考慮したパターン２。forの前に判断
list?.let {
    for (i in it) {
    }
}
```
### イテレータの自作
規定のメソッドが実装されていればイテレータを備えるクラスを自作できる
``` kotlin
fun main(args: Array<String>) {
    for(item in Iterator()) {
        println(item)
    }
}

class IteratorFunctions {
    operator fun hasNext(): Boolean = Math.random() < 0.8
    operator fun next(): String = "unko"
}

class Iterator {
    operator fun iterator() = IteratorFunctions()
}
```

### while
お馴染みの前判断、後判断、どっちもいけますが
後判断のスコープが便利になってます。
``` kotlin
// 前判断
while (x > 0) {

}

// 後判断
do {
    val y = retrieveData()
} while (y != null) // yが見える！
```

## 範囲指定 range
```kotlin
// ｘが１〜１0
if(x in 1..10)
    println("ok")

// ｘが１〜１0じゃない
if(x !in 1..10)
    println("ng")

// リスト
println((1..5).toList())               // [1, 2, 3, 4, 5]
println((1..5).reversed().toList())    // [5, 4, 3, 2, 1]
println((5 downTo 1).toList())         // [5, 4, 3, 2, 1]
println((1..5 step 2).toList())        // [1, 3, 5]
```

## 配列 array
``` kotlin
// お好みで
val list = arrayOf(1, 2, 3)               // 型は類推される
val list = intArrayOf(1, 2, 3)            // intで
val list: Array<Int?> = arrayOfNulls(3)   // nullな要素を３っつ

list[0] = list[1] + list[2]       // 各要素はお馴染みのカッコで

for(item in list){                // forループくるくる
    println(item)
}
```

## コレクション collection
### list（重複要素あり）
``` kotlin
val list = listOf(1, 2, 3)
list[0] = list[1] + list[2]    // immutable（変更不可）エラー

val list = mutableListOf(1, 2, 3)
list[0] = list[1] + list[2]    // mutalbe（変更可能）

val list = mutableListOf<Hoge>() // 空っぽでinitialize
```

### set（重複要素なし）
```kotlin
val list = setOf(1, 2, 2, 3)  // immutable（変更不可）変更する場合はmutableSetOf
for(num in list)
    print(num)  // 123
```
### map（キーと値のペア）
``` kotlin
val map = mapOf(    // immutalbe（変更不可）。変更する場合はmutableMapOf
    1 to "one",
    2 to "two",
    3 to "three"
)
//for(item in map){
//    println("${item.key} to ${item.value}")
//}
for((key, value) in map)
    println("${key} to ${value}")

println(list[1])
```
結果
``` kotlin
1 to one
2 to two
3 to three
one
```

## データクラス data class
値を保持するだけのクラスならこれで。クラス名の前にdataを付けます。

``` kotlin
data class User(val name: String = "", val age: Int = 0)
```
使い方
``` kotlin
val jack = User(name = "Jack", age = 1)  // jackさん１歳
val olderJack = jack.copy(age = 2)       // jackさんの名前のまま２歳のコピーを

val jane = User("Jane", 35)  // janeさん３５歳
val (name, age) = jane       // janeさんの名前、年齢をGET！
```
copy用の関数が作られるみたい
```kotlin
fun copy(name: String = this.name, age: Int = this.age) = User(name, age)
constructor を追加して使いやすく

    data class User(val name: String = "", val age: Int = 0) {
        constructor(name: String, age: Int, email: String) : this(name, age)
    }
```

## enumクラス
``` kotlin
enum class Direction {
    NORTH, SOUTH, WEST, EAST
}
```
定義と初期化
``` kotlin
enum class Color(val rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF)
}
```
ちょっと使いやすく
```kotlin
enum class HogeType constructor(val value: Int) {
    AAA(0),
    BBB(1),
    CCC(2);

    companion object {
        fun fromInt(value: Int): HogeType {
            return values().firstOrNull { it.value == value } ?: AAA
        }
    }

    val isAAA: Boolean
    get() = this == AAA

    val isBBB: Boolean
    get() = this == BBB
}
```

## シングルトン singleton
``` kotlin
object SingletonUser {
    private var name: String = "ssuzaki"

    fun init(data: String) {
        name = data
    }

    fun put() {
        println("${name}")
    }
}

fun main(args: Array<String>) {
    SingletonUser.put()
}
```

## コンパニオンオブジェクト companion
``` kotlin
class MyClass {
    companion object { }
}

fun MyClass.Companion.foo() {
    println("hoge")
}

fun main(args: Array<String>) {
    MyClass.foo()
}
```

## 同一 equality
同じ参照先か===で比較。違う参照先は!==
``` kotlin
val taro = User("taro", 10)
val jiro = User("jiro", 11)

if(taro === jiro)
    println("taro equal jiro")
```

## 例外 Exceptions
例外はすべて Throwable の子孫でメッセージ、スタックトレースを持ち
オプションで原因を持ちます。

### 例外を投げる throw
``` kotlin
throw MyException("Hi There!")
```

### 例外を捕捉する try...catch...finally
``` kotlin
try {
    // some code
} catch(e: SomeException) {
    // handler
} finally {
    // optional finally block
}
```

### tryは式で値を返せる
``` kotlin
val a: Int? = try { parseInt(input) } catch (e: NumberFormatException) { null }
```

## クラス class
``` kotlin
class Hoge {
    // プロパティの定義。getterとsetterが定義される。valならgetterのみ
    var name: String = ""

    // コンストラクタ
    constructor(name: String) {
        this.name = name
    }

    // メソッドの定義
    fun changeLanguage(language: String) {
    }
}
```

### プライマリコンストラクタ
``` kotlin
class Hoge(n: String) {
    val name = n
}

// プライマリコンストラクタでプロパティも一緒に定義するケース
class Hoge(val name: String) {
}
```

### クラスのネスト
``` kotlin
class Hoge {
    val num: Int

    // 外側のクラスのメンバを参照するときはinner classにしないと参照できない
    inner class Fugo {
        val total = num + 10

        // inner class から外側のクラスのthisを指したいときは@で指定
        // this@Hoge
    }
}
```
### 継承
``` kotlin
// openを付けないと継承できない
open class Base {
}

class Hoge : Base() {
}
```

## インターフェイス interface
``` kotlin
interface Hoge {
    fun hoge()
}

// javaでのimplementsは:で
class Sample: Hoge {
    override fun hoge() {
        println("gorua-")
    }
}

// 無名クラスで実装↓
class Sample {
    private val h = object: Hoge {
        override fun hoge() {
            println("gorua-")
        }
    }
}
```

## キャスト cast
``` kotlin
val hoge = obj as Hoge
```

## スコープ関数 Scope Functions
### let　（nullじゃなかったら○○したい）
null-typeの変数と一緒に、nullじゃなかったら○○したいシチュエーションで
``` kotlin
// これが
if (hoge != null) {
    textView.text = hoge.name
}

// こう書ける
hoge?.let {
    textView.text = it.name
}
```
``` kotlin
var list: MutableList<Int>? = null
list?.let {
    println(it)  // nullなので出力されない。クラッシュしないよ。
}

list = mutableListOf (1, 2, 3)
list?.let {
    println(it)  // nullじゃないので出力される。
}
```
