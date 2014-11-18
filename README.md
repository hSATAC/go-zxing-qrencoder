go-zxing-qrencoder
==================

ZXing QRCode Encoder Implementation in Go

This project aims to replicate and be fully compitable with [ZXing](https://github.com/zxing/zxing) QRCode Encoder version 3.1 in Golang. We want to make sure the generated QRCode is exactly the same with the Java version's.

Lots of the source code was forked from [qrencode-go](https://github.com/qpliu/qrencode-go)

## Example

```
package main

import (
	"github.com/hSATAC/go-zxing-qrencoder/qrencode"
	"image/png"
	"os"
)

func main() {
	str := "I <3 Github."

	grid, err := qrencode.Encode(str, qrencode.ECLevelQ)
	if err != nil {
		return
	}
	f, err := os.Create("example.png")
	if err != nil {
		return
	}
	defer f.Close()
	png.Encode(f, grid.Image(5))
}
```

## TODO

* Encoding is hard-coded to `ISO-8895-1` now, need to finish the ECI header part.
