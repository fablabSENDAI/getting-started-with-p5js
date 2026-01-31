---
layout: default
title: Color - 色
nav_order: 6
has_children: true
---

# Color : 色

手始めに背景色を変更してます。

```js
function setup() {
  createCanvas(500, 400);
}

function draw() {
  //set background color by gray scale 0~255
  background(80);
  
  //set background color by RGB 0~255
  //background(181,75,72);

  //set back ground color by hex color code
  //background('#219967');
}
```
###### ※コメント部分で無効にされているコードを有効にすると違いが見れます。

↓そのまま実行した結果

![](./images/02_color/01-background.png)

**background()** 関数は指定した色を背景色にします。
指定の仕方は複数あり...

•グレースケールで指定(値:0~255)<br>
**background(Grayscale)**

•RGBで指定(値:0~255)<br>
**background(R,G,B)**

•HEXカラーコードで指定([Adobe color](https://color.adobe.com/ja/create/color-wheel)をつかうと便利)<br>
**background('HEX')**
