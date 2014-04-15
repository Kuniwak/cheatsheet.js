# 文字列処理
## 文字列操作
### 長さ
文字列の長さは `length` プロパティで取得できる。

```javascript
'foo'.length // -> 3
```

### 1文字の取得
文字列の1文字の取得は `[]` リテラルと `String#charAt(index)` メソッドの2つがある。

```javascript
'foobar'[3] // -> 'b'
'foobar'.charAt(3) // -> 'b'

'foobar'[100] // -> undefined
'foobar'.charAt(100) // -> ''
```

### 結合
`+` 演算子を使う方法と、`Array#join` を使う2パターンがある。

```javascript
'foo' + 'bar' // -> 'foobar'
```

```javascript
var str = 'foo';
str += 'bar' // -> 'foobar'
```

```javascript
['foo', 'bar'].join();   // -> 'foo,bar'
['foo', 'bar'].join(''); // -> 'foobar'
```

### 繰り返し
JavaScriptに文字列繰り返し演算はない。

```javascript
function repeat(str, num) {
  return Array(num + 1).join(str);
}
```

### 切り出し
文字列の切り出し関数は複数ある。

 * `String#slice(start, end)`
 * `String#substring(start, end)`

```javascript
'foohogebar'.slice(3)         // -> 'hogebar'
'foohogebar'.slice(-3)        // -> 'bar'

'foohogebar'.slice(3, 7)      // -> 'hoge'
'foohogebar'.slice(3, -3)     // -> 'hoge'

'foohogebar'.substring(3)     // -> 'hogebar'
'foohogebar'.substring(3, 7)  // -> 'hoge'
'foohogebar'.substring(3, -3) // -> 'hogebar'
```

※ `String#substr` もあるが、ECMA Scriptに記載されておらず非推奨。

### 文字列置換
文字列の置換には `String#replace(expr, str)` をつかう。

`expr` には文字列、正規表現を指定できる（文字列・正規表現でないオブジェクト・値の場合は文字列に暗黙にキャストされる）。
`str` には文字列、関数がつかえる（文字列・関数でないオブジェクト・値の場合は文字列に暗黙にキャストされる）。

```javascript
'fooHOGEbar'.replace(/H..E/, 'HOGEHOGE') // -> 'fooHOGEHOGEbar'
'fooHOGEbar'.replace('HOGE', 'HOGEHOGE') // -> 'fooHOGEHOGEbar'
'fooHOGEbar'.replace('HOGE', function(match) { return match + 'HOGE'; }) // -> 'fooHOGEHOGEbar'
```

### 数値変換
数値変換には3種類のやり方がある。

 * 整数変換：
   * `parseInt(str)`
 * 浮動小数点変換：
   * `Number(str)`
   * `parseFloat(str)`

```javascript
Number('10.1') // -> 10.1
parseInt('10.1') // -> 10
parseFloat('10.1') // -> 10.1
```

## 文字列比較
### 文字列判定
文字列の判定には `typeof` 演算子をつかう。

```javascript
typeof 'foobar' === 'string' // -> true
typeof 100 === 'string'      // -> false
```

### 等価比較
文字列の等価比較には、`===` と `==` があるが、`===` のほうが望ましい。

```javascript
'foo' === 'foo' // -> true
'foo' === 'bar' // -> false
```

`==` 演算子には予期せぬ挙動がある。
```javascript
'' == 0     // -> true
'0' == [0]  // -> true

'' === 0    // -> false
'0' === [0] // -> false
```

### 位置検索
部分文字列の検索には、`String#indexOf(str)` をつかう（正規表現を使うこともできる）。

```javascript
'foohogebar'.indexOf('hoge')     // ->  3
'foohogebar'.indexOf('hogehoge') // -> -1
```
