# README_JavaScript
# 言語化
## Fetch
document.getElementById、このメソッド（add-button）を取得してこのボタンが押された（click）時に、この関数（onClickAdd）を実行します。

※補足　getElementById（"idを取得できる"）

※補足　addEventListener（"イベントの種類", 実行処理）下記の文では二つの引数を取得していますが厳密には三つまで引数を取得することが可能です。
#### ソースコード
```
//index.js

const onClickAdd = () => {
  alert();
};

document.getElementById("add-button").addEventListener("click", onClickAdd);

```
```
//index.html

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ボタン</title>
  </head>
  <body>
    <button id="add-button">追加</button>
  </body>
</html>

```
## DOM操作
下記の文章ではinputTextにその時、入力されている値にアクセスできます。

また、その応用でinputTextの中身を初期化することもできます。
```
  // テキストボックスの値を取得し、初期化する
const inputText = document.getElementById("add-text").value;
document.getElementById("add-text").value = "";
```
### タグの生成
console.log(li);でタグが生成されていることを確認することができます。

javascriptにDOM生成したdivにクラスをつけることもできます。

p.innerText = inputText;のようにしてあげることで、変数名（inputText）の文字列を参照してくれます。

```
  // li生成
  const li = document.createElement("li");

  // div生成
  const div = document.createElement("div");
  div.className = "list-row";

  // p生成
  const p = document.createElement("p");
  p.className = "todo-item";
  p.innerText = inputText;
```
### 階層構造

javascriptには、タグの階層構造（appendChild();）を設定してあげることでDOMに対して階層構造を持たせることができます。

htmlの方のulタグにidを付与してjavascriptにidをfetchしてあげて、incomplete-listはliの一つ階層上の親ですよと明示的に記述してあげることで、DOMをhtmlに差し込むことができます。

```
  // liタグの子要素に各要素を設定
  div.appendChild(p);
  li.appendChild(div);

  // 未完了のリストに追加
  document.getElementById("incomplete-list").appendChild(li);
```
#### ソースコード
```
//index.js

const onClickAdd = () => {
  // テキストボックスの値を取得し、初期化する
  const inputText = document.getElementById("add-text").value;
  document.getElementById("add-text").value = "";

  // li生成
  const li = document.createElement("li");

  // div生成
  const div = document.createElement("div");
  div.className = "list-row";

  // p生成
  const p = document.createElement("p");
  p.className = "todo-item";
  p.innerText = inputText;

  // liタグの子要素に各要素を設定
  div.appendChild(p);
  li.appendChild(div);

  // 未完了のリストに追加
  document.getElementById("incomplete-list").appendChild(li);
};

document.getElementById("add-button").addEventListener("click", onClickAdd);

```

```
//index.html

<!DOCTYPE html>
<html lang="en">
  <head>
    <link rel="stylesheet" href="styles.css" />
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Todoアプリ</title>
  </head>
  <body>
    <div class="input-area">
      <input id="add-text" placeholder="Todoを入力" />
      <button id="add-button">追加</button>
    </div>
    <div class="incomplete-area">
      <p class="title">未完了のTODO</p>
      <ul id="incomplete-list">
        <li>
          <div class="list-row">
            <p class="todo-item">TODOです</p>
            <button>完了</button>
            <button>削除</button>
          </div>
        </li>
        <li>
          <div class="list-row">
            <p class="todo-item">TODOです</p>
            <button>完了</button>
            <button>削除</button>
          </div>
        </li>
      </ul>
    </div>
    <div class="complete-area">
      <p class="title">完了のTODO</p>
      <ul>
        <li>
          <div class="list-row">
            <p class="todo-item">TODOでした</p>
            <button>戻す</button>
          </div>
        </li>
      </ul>
    </div>
    <script src="./index.js"></script>
  </body>
</html>

```
