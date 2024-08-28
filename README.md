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
import { CorrectLevel, QRCode } from '@jswork/qrjs';

const qrcode = new QRCode(-1, ErrorCorrectLevel.H);
qrcode.addData("afei");
qrcode.make();
```

## with canvas
```js
import { CorrectLevel, QRCode } from '@jswork/qrjs';

const canvas = document.getElementById('qrcode');
const qrcode = new QRCode(canvas, -1, ErrorCorrectLevel.H);
qrcode.addData("afei");
qrcode.make();
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
