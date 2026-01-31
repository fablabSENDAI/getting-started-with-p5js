---
layout: default
title: Color02 - RGBとHSB
parent: Color - 色
nav_order: 2
---


# Color02:RGBとHSB

通常 **fill()** や **stroke()** の値はRGBで指定しますが、<br>**colorMode()** 関数を使用することで、
**色相(Hue)•彩度(Saturation)•明度(Brightness)** で色指定を行うことも可能です。

```js
function setup() {
  createCanvas(500, 400);
  
  noLoop();
}

function draw() {
  background(200);

  colorMode(RGB); //dafault
  fill(55,219,152); //change fill color
  ellipse(150,200,150,150); // draw circle

  colorMode(HSB,255); //color by Hue/Saturation/Brightness
  fill(55,219,152); //change fill color
  ellipse(350,200,150,150); // draw circle
}
```

実行結果↓

![](../images/02_color/06-colorMode.png)

**colorMode(RGB);** と書いた行以降は、RGB指定による色の選択になるため、<br>
**fill(R,G,B);** として認識され(こちらがデフォルトの状態)<br>
↓<br>
**colorMode(HSB);** と書いた行以降は、色相•彩度•明度指定による色の選択になるため、<br>
**fill(色相,彩度,明度);** として認識されます<br>
...これが、同じ値をfill()に書き入れているのにも関わらず色が違う原因です。