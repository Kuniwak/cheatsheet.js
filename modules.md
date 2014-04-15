# モジュール

*javascriptにモジュールなんてものは存在しない*









## とりあえずのモジュール化

globalなオブジェクトにメンバを生やして名前空間の代わりにする。

```javascript

// ブラウザ実行とNode.js環境でglobalオブジェクトの名前が異なる
var global = window || this;

global.jp = {} || global.jp;
global.jp.co = {} || global.jp.co;
global.jp.co.mixi = {} || global.jp.co.mixi;

global.jp.co.mixi.Class = function(){
	// ここにコンストラクタ
};
```
