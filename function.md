# 関数処理
## 関数定義
関数を定義する構文は2つある。
慣例的にコンストラクタではない関数の名前は先頭が小文字のキャメルケースで書く（従わなくても動くが、可読性が下がる）。

 * 関数式：

   引数等に指定する場合は、無名関数の関数式をつかうことが多い。

   ```javascript
   function() {}
   ```

   関数式を利用して、無名関数を変数代入してもよい。

   ```javascript
   var myFunc = function() {
     return 'hoge';
   };

   myFunc() // -> 'hoge'
   ```

 * 関数宣言文：`function`

   ```javascript
   function myFunc() {
     return 'hoge';
   }

   myFunc() // -> 'hoge'
   ```

## コンストラクタ
コンストラクタはただの関数である。
関数を呼び出す際に `new` 演算子を前置すると、コンストラクタとして呼び出される。
慣例的にコンストラクタの名前は先頭が大文字のキャメルケースで書く（従わなくても動くが、可読性が下がる）。

```javascript
var King = function() {
  this.name = 'King';
  this.guessLevel = 10e9;
};

var king = new King();
king.name       // -> 'King'
king.guessLevel // -> 10e9
```
