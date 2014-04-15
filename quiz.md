# Quiz

与えられた数までのフィボナッチ数列を返す関数を作成してください：

`answerCode(4) // -> '1, 1, 2, 3, 5'`

応えは、下のコードの `// Write your code.` の部分に記入してください。

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JavaScript Quiz</title>
</head>
<body>
  <div id="target"></div>
  <script>
    var answerCode = function() {
      // Write your code.
    };

    var target = document.getElementById('target');
    var end = Math.floor(Math.random() * 100);
    target.innerText = answerCode(end);
  </script>
</body>
</html>
```
