# qrjs
> A wrapper for qr.js.

[![version][version-image]][version-url]
[![license][license-image]][license-url]
[![size][size-image]][size-url]
[![download][download-image]][download-url]

## installation
```shell
npm install @jswork/qrjs
```

## usage
```js
import { Level, QRCode } from '@jswork/qrjs';

const qrcode = new QRCode(-1, Level.H);
qrcode.addData("afei");
qrcode.make();
```

## with canvas
> yarn add canvas

```js
import { Level, QRCode } from '@jswork/qrjs';
import { createCanvas } from "canvas";
import fs from "fs";

// 生成二维码
const qrcode = new QRCode(-1, Level.H);
qrcode.addData("afei");
qrcode.make();

// 获取二维码模块的大小和数据
const size = qrcode.getModuleCount();
const cellSize = 10; // 每个模块的大小，调整这个值可以改变二维码的尺寸
const margin = 4 * cellSize; // 留白的大小

// 创建Canvas
const canvas = createCanvas(
  size * cellSize + margin * 2,
  size * cellSize + margin * 2
);
const ctx = canvas.getContext("2d");

// 绘制二维码背景
ctx.fillStyle = "#ffffff";
ctx.fillRect(0, 0, canvas.width, canvas.height);

// 绘制二维码
ctx.fillStyle = "#000000";
for (let row = 0; row < size; row++) {
  for (let col = 0; col < size; col++) {
    if (qrcode.isDark(row, col)) {
      ctx.fillRect(
        margin + col * cellSize,
        margin + row * cellSize,
        cellSize,
        cellSize
      );
    }
  }
}

// 保存为PNG文件
const out = fs.createWriteStream("qrcode.png");
const stream = canvas.createPNGStream();
stream.pipe(out);
out.on("finish", () => console.log("QR code PNG file generated: qrcode.png"));
```

## license
Code released under [the MIT license](https://github.com/afeiship/qrjs/blob/master/LICENSE.txt).

[version-image]: https://img.shields.io/npm/v/@jswork/qrjs
[version-url]: https://npmjs.org/package/@jswork/qrjs

[license-image]: https://img.shields.io/npm/l/@jswork/qrjs
[license-url]: https://github.com/afeiship/qrjs/blob/master/LICENSE.txt

[size-image]: https://img.shields.io/bundlephobia/minzip/@jswork/qrjs
[size-url]: https://github.com/afeiship/qrjs/blob/master/dist/index.min.js

[download-image]: https://img.shields.io/npm/dm/@jswork/qrjs
[download-url]: https://www.npmjs.com/package/@jswork/qrjs
