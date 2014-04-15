# 変数

*値につける別名* というイメージ。
C的な「値の入れ物」という概念ではない気がする。

## 宣言

```javascript
	var a = 777;
```

`var` キーワードを付けないと、現在のスコープを支配しているオブジェクトのメンバとして、変数が作成されてしまう。
（`with`文を使うなど特殊なことをしない限りは、ブラウザであれば`window`オブジェクト、Node.js環境であれば`global`オブジェクトが支配オブジェクトになる）

## リテラル

```javascript
	// 真偽値(Boolean)
	// 0, null, "" (null string), undefindeはfalseとして扱われるので注意
	var bool = true || false;

	// 整数も実数も、どちらもNumberオブジェクト
	var num = 123.45;

	// 文字列はStringオブジェクト
	var str = "hello world";

	// 配列(Array)の中身はひとつの型で統一されている必要はない
	// （バグを招くので、統一することを強くおすすめする）
	var array = [false, 1, "two", 3.0];

	// オブジェクト(Object)は、他言語でいうところのハッシュ（マップ、ディクショナリ）に該当する
	var obj = {
		foo:	"bar"
	};

	// 関数(Function)はjavascriptのキモ
	// 無名関数を使うことが多い
	var fnc = function(arg) {
		return "にゃんぱすー";
	};
```
