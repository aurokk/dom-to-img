# DOM to SVG

![license: MIT](https://img.shields.io/npm/l/dom-to-svg)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![npm](https://img.shields.io/npm/v/@aurokk/dom-to-svg)](https://www.npmjs.com/package/@aurokk/dom-to-svg)

Library to convert a given HTML DOM node into an accessible SVG "screenshot".

PLEASE NOTE: IT IS A FORK OF [felixfbecker/dom-to-svg](https://github.com/felixfbecker/dom-to-svg) THAT I WANT TO ACTUALIZE AND IMPROVE. THERE IS NO TESTS AND IT IS UNSTABLE, SO DO NOT USE IT IN PRODUCTION. I WILL REMOVE THAT MESSAGE WHEN IT IS READY. THANKS.

## Usage

```js
import { documentToSVG, elementToSVG, inlineResources, formatXML } from 'dom-to-svg'

// Capture the whole document
const svgDocument = documentToSVG(document)

// Capture specific element
const svgDocument = elementToSVG(document.querySelector('#my-element'))

// Inline external resources (fonts, images, etc) as data: URIs
await inlineResources(svgDocument.documentElement)

// Get SVG string
const svgString = new XMLSerializer().serializeToString(svgDocument)
```

The output can be used as-is as valid SVG or easily passed to other packages to pretty-print or compress.

## Features

- Does NOT rely on `<foreignObject>` - SVGs will work in design tools like Illustrator, Figma etc.
- Maintains DOM accessibility tree by annotating SVG with correct ARIA attributes.
- Maintains interactive links.
- Maintains text to allow copying to clipboard.
- Can inline external resources like images, fonts, etc to make SVG self-contained.
- Maintains CSS stacking order of elements.
- Outputs debug attributes on SVG to trace elements back to their DOM nodes.
