# リスト・マップ処理

## リテラル

配列は`[]`、マップ（オブジェクト）は`{}`。
jsではマップという言葉は使わない。基本的にオブジェクトと呼ぶ。
（マップは別に使われているため）

```javascript
	var array = [];
	var obj = {};
```

## 要素参照

配列の参照は一般的なC系の言語と同じ。

オブジェクトの要素参照は二通りの方法がある。

1. `[]`の中に文字列でキー値を与える(PHP風)
2. メンバ参照

```javascript
	var array = [1, 2, 3, 4];
	console.log(array[2]);	// -> 3

	var obj = {
		hoge:	"huga",
		foo:	"bar"
	};
	console.log(obj["hoge"]);	// -> "huga"
	console.log(obj.foo);		// -> "bar"
```

## 繰り返し

### 配列

for文を使う方法と、`Array.prototype.map()`を使う方法がある。

`map()`の引数は、配列の各要素にアクセスされた際に呼び出されるコールバック関数。コールバック関数の引数は、配列の要素とそのインデックス番号。

```javascript
	var array = [1, 2, 3, 4];
	for (var i = 0; i < array.length; i++) {
		console.log(array[i]);
	}
	// -> 1 2 3 4

	array.map(function(val, idx) {
		console.log(val);
	});
	// -> 1 2 3 4
````

### オブジェクト

繰り返しというよりかは列挙。
for文で`in`キーワードを使うことでメンバを列挙しながら繰り返しができる。

本来は、特定の名前のメンバに対してデータを与えるためのデータ構造なので、メンバの列挙はしないほうがいい気がする。

```javascript
	var obj = {
		hoge:	"huga",
		foo:	"bar"
	};

	for (var key in obj) {
		console.log(obj[key]);
	}
```

## 結合

### 配列

`Array.prototype.concat()`を使う。

```javascript
	var a = ["hoge", "fuga"];
	var b = ["foo", "bar"];
	var c = a.concat(b);

	console.log(c);	// -> ["hoge", "fuga", "foo", "bar"]
```

### オブジェクト

結合ではなく *extend* や *merge* と言われることが多い。
専用のメソッドはないので、自力で実装するか、jQueryなどのライブラリを使うのが一般的。

```javascript
	var a = {
		hoge:	"huga",
		foo:	"bar"
	};
	var b = {
		nemui:	"zzzzzz",
		harahe:	"goooooo"
	};

	var c = {};
	for(var keyOfA in a) {
		c[keyOfA] = a[keyOfA];
	}
	for(var keyOfB in b) {
		c[keyOfB] = b[keyOfB];
	}

	console.log(c);
	// -> {hoge: "huga", foo: "bar", nemui: "zzzzzz", harahe: "goooooo"}
````

## 切り出し
### 配列

`Array.prototype.slice()` または `Array.prototype.splice()` を使う。
`Array.prototype.splice()`は破壊的メソッドなので注意（配列の内容が変化する）。

```javascript
	var array = [1, 2, 3, 4, 5];

	var oneToThree = array.slice(1, 3);	// -> [2, 3]

	var afterOfOne = array.splice(1);
	// array -> [1]
	// afterOfOne -> [2, 3, 4, 5];
```

### オブジェクト

範囲指定する方法がないので、切り出しに該当する手法はない。

メンバを削除する方法はある。

```javascript
	var obj = {
		hoge:	"huga",
		foo:	"bar"
	};

	delete obj.hoge;
	// obj -> {foo: "bar"}
```

## NodeListとArrayの違い

`Array`はいわゆる配列として使われている。

`NodeList`は配列のアクセス演算子で要素にアクセスできるが、`Array`とは異なるオブジェクトである。
主にDOM (Document Object Model)におけるNodeを格納するためのオブジェクト。

```javascript
	var anchors = document.getElementsByTagName("a");	// -> aタグ
	console.log(anchors[0]);	// -> docuemnt中に初めて出現するaタグを得る

	// Arrayと同じくlengthプロパティを持っているので
	// 要素数を知る事ができる
	for(var i = 0; i < anchors.length; i++) {
		console.log(anchors[i]);
	}

	// Arrayのようなmap()メソッドは持っていない。
	// Array.prototype.map()を借りてきて使うことはできる。
	Array.prototype.map.call(anchors, function(elem) {
		console.log(elem);
	});
```
