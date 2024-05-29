# README_JavaScript
## 言語化
document.getElementById、このメソッド（add-button）を取得してこのボタンが押された（click）時に、この関数（onClickAdd）を実行します。

※補足　addEventListener下記の文では二つの引数を取得していますが厳密には三つまで引数を取得することが可能です。
```
const onClickAdd = () => {
  alert();
};

document.getElementById("add-button").addEventListener("click", onClickAdd);

```
