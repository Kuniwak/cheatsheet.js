# クラス

javascriptにはクラスという概念が存在しないので、functionオブジェクトとprototypeチェーンを使用してクラスのように使えるオブジェクトを作成する必要がある。

```javascript
	// クラス宣言
	var Foo = (function(){

		// Fooクラスのコンストラクタ
		var Foo = function(a){

			// public: なメンバ変数 bar（パブリックなメンバ変数）
			this.bar = a;

			// private: なメンバ変数 _baz（プライベートなメンバ変数）
			this._baz = "initial value";
		};

		// public: なメソッド qux
		Foo.prototype.qux = function(){
		  console.log(this.bar);
		};

		// private: なメソッド _foobar
		Foo.prototype._foobar = function(){
			console.log("foo" + this.bar);
		};

		// public: static なメンバ変数 Hoge（パブリックなクラス変数）
		Foo.Hoge = "this is public";

		// public: static なメソッド Fuga（パブリックなクラスメソッド）
		Foo.Fuga = function(){
			console.log("this is public class method");
		};

		// private: static なメンバ変数 Moge（プライベートなクラス変数）
		var Moge = "this is private";

		// private: static なメソッド Piyo（プライベートなクラスメソッド）
		var Piyo = function(){
			console.log("this is private class method.");
		};

		return Foo;
	})();

	// インスタンス生成
	var foo = new Foo("bar);
```

解説は [kikuchyが昔書いた記事](http://kikuchy.hatenablog.com/entry/2013/07/31/185808) があるのでそちらを参照されたし。
