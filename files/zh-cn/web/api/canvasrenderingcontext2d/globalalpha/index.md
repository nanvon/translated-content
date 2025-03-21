---
title: CanvasRenderingContext2D.globalAlpha
slug: Web/API/CanvasRenderingContext2D/globalAlpha
---
{{APIRef}}

**`CanvasRenderingContext2D.globalAlpha`** 是 Canvas 2D API 用来描述在 canvas 上绘图之前，设置图形和图片透明度的属性。 数值的范围从 0.0（完全透明）到 1.0（完全不透明）。

在 [Canvas Tutorial](/zh-CN/docs/Web/API/Canvas_API/Tutorial) 中参见 [Applying styles and color](/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors) 章节。

## 语法

```
ctx.globalAlpha = value;
```

### 选项

- `value`
  - : 数字在 0.0 （完全透明）和 1.0（完全不透明）之间。 默认值是 1.0。如果数值不在范围内，包括{{jsxref("Infinity")}} 和{{jsxref("NaN")}} ，无法赋值，并且 `globalAlpha` 会保持原有的数值。

## 示例

### 使用 `globalAlpha` 属性

这是一段使用 `globalAlpha` 属性的简单代码片段，绘制了 2 个半透明的矩形。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");

ctx.globalAlpha = 0.5;

ctx.fillStyle = "blue";
ctx.fillRect(10, 10, 100, 100);

ctx.fillStyle = "red";
ctx.fillRect(50, 50, 100, 100);
```

修改下面的代码并在线查看 canvas 的变化：

```html hidden
<canvas id="canvas" width="400" height="200" class="playable-canvas"></canvas>
<div class="playable-buttons">
  <input id="edit" type="button" value="Edit" />
  <input id="reset" type="button" value="Reset" />
</div>
<textarea id="code" class="playable-code" style="height:120px;">
ctx.globalAlpha = 0.5;

ctx.fillStyle = "blue";
ctx.fillRect(10, 10, 100, 100);

ctx.fillStyle = "red";
ctx.fillRect(50, 50, 100, 100);</textarea>
```

```js hidden
var canvas = document.getElementById("canvas");
var ctx = canvas.getContext("2d");
var textarea = document.getElementById("code");
var reset = document.getElementById("reset");
var edit = document.getElementById("edit");
var code = textarea.value;

function drawCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  eval(textarea.value);
}

reset.addEventListener("click", function() {
  textarea.value = code;
  drawCanvas();
});

edit.addEventListener("click", function() {
  textarea.focus();
})

textarea.addEventListener("input", drawCanvas);
window.addEventListener("load", drawCanvas);
```

{{ EmbedLiveSample('Playable_code', 700, 380) }}

### `globalAlpha` 例子

此例中，绘制了 4 个不同背景色的正方形。在他们上面，绘制半透明的圆形。将那个点绘制的所有图形的 `globalAlpha` 属性值都设置为 0.2。通过 for 循环绘制半径逐渐增大的圆形。 最终形成的结果是放射性渐变。通过不停地叠加圆形， 使得先前绘制的圆形的透明度越来越暗。通过增加循环数量绘制更多的圆形，图片中心的背景将会变成完全不透明。

```js
var ctx = document.getElementById('canvas').getContext('2d');

// draw background
ctx.fillStyle = '#FD0';
ctx.fillRect(0,0,75,75);
ctx.fillStyle = '#6C0';
ctx.fillRect(75,0,75,75);
ctx.fillStyle = '#09F';
ctx.fillRect(0,75,75,75);
ctx.fillStyle = '#F30';
ctx.fillRect(75,75,75,75);
ctx.fillStyle = '#FFF';

// set transparency value
ctx.globalAlpha = 0.2;

// Draw semi transparent circles
for (i=0;i<7;i++){
  ctx.beginPath();
  ctx.arc(75,75,10+10*i,0,Math.PI*2,true);
  ctx.fill();
}
```

```html hidden
<canvas id="canvas" width="150" height="150"></canvas>
```

{{EmbedLiveSample("A_globalAlpha_example", "180", "180", "https://mdn.mozillademos.org/files/232/Canvas_globalalpha.png")}}

## 规范描述

{{Specifications}}

## 浏览器兼容性

{{Compat("api.CanvasRenderingContext2D.globalAlpha")}}

## 参见

- 接口定义，{{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.globalCompositeOperation")}}
