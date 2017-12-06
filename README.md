# js-blp
This module provides functionality for reading texture files associated with Blizzard games (.blp) in JS and Node.

## Installing
NodeJS
```
npm install js-blp
```

Web JS
```html
<script type="text/javascript" src="bufo.js"></script>
<script type="text/javascript" src="js-blp.js"></script>
```

## Example Usage
NodeJS
```javascript
const fs = require('fs');
const BLPFile = require('js-blp');

// Check Bufo documentation for other ways to provide data beyond fs.
let blp = new BLPFile(fs.readFileSync('cat.blp'));

// Metadata can be accessed after construction..
console.info({
	"width": blp.width,
	"height": blp.height,
	"encoding": blp.encoding,
	"alphaEncoding": blp.alphaEncoding,
	"alphaDepth": blp.alphaDepth,
	"mipmapCount": blp.mapCount
});

// Data is requested for a specific mipmap..
let data = blp.getPixels(0);

// data is an instance of Bufo containing the pixel data in the format:
// [ R, G, B, A, R, G, B, A, R, G, B, A ... ]
```