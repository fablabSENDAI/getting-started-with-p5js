---
layout: default
title: ExportSvg00 - 原寸大出力
parent: ExportSVG - SVG書き出し
nav_order: 1
---

# ExportSvg00 - 原寸大出力

## 【寸法ずれてしまう問題】

p5js内部で扱われる寸法は基本的に **px (ピクセル)** です。<br>

そして、都合の悪いことに、<br>

**1px ≠ 1mm** 

なので、直径30mmの円として書き出したい時に、p5js側で

```js
    ellipse(width/2, height/2, 30, 30);
```

と書いてもイラレ側でそのSVGデータを読み込むとスケールがずれてしまいます。

## 【mmをpxに変換してくれる関数】

そこで、mmの値をpxに変換してくれる関数を導入します。<br>
以下のコードを、スケッチの最後 (drawの閉じカモメ括弧 → **}** よりも下) に追加します。

```js
    //convert mm to pixel
function mmToPixel(mm,dpi = 96) {
  //Inkscape = 96dpi
  //Adobe = 72dpi
  
  let inch = mm / 25.4;
  let px = inch * dpi;
 
  return px;
}
```

## 【サンプルコード】
試しに以下のサンプルを実行してみてください。

```js
p5.disableFriendlyErrors = true; // hush

function setup() {
  createCanvas(mmToPixel(146), mmToPixel(89));
  
   noLoop();
}

function draw() {
  strokeWeight(1);
  stroke(0);
  noFill();
  beginRecordSvg(this, "myOutput.svg");
  
  ellipse(width/2, height/2, mmToPixel(40), mmToPixel(40));
  
  endRecordSvg();
  
}


//convert mm to pixel
function mmToPixel(mm,dpi = 96) {
  //Inkscape = 96dpi
  //Adobe = 72dpi
  
  let inch = mm / 25.4;
  let px = inch * dpi;
 
  return px;
}
```

イラレで開いてみると、直径40mmピッタリの円のパスデータが出力できているはずです。