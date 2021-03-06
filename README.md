Go Imagick
==========

Go Imagick is a Go bind to ImageMagick's MagickWand C API.

It was originally developed and tested with ImageMagick 6.8.5-4, however most official Unix or Linux distributions use older
versions (6.7.7, 6.8.0, etc) so some features in Go Imagick's go1 branch are being commented out and will see the light when
these ImageMagick distributions could easily be updated (from the devops PoV).

### Install

#### Mac OS X

MacPorts

```bash
$ sudo port install ImageMagick
```

#### Ubuntu / Debian

```bash
$ sudo apt-get install libmagickwand-dev
```

#### Common

Check if pkg-config is able to find the right ImageMagick include and libs:

```bash
$ pkg-config --cflags --libs MagickWand
```

Then go get it:

```bash
$ go get github.com/gographics/imagick/imagick
```

### API Doc

http://godoc.org/github.com/gographics/imagick/imagick

### Examples

The examples folder is full with usage examples ported from C ones found in here: http://members.shaw.ca/el.supremo/MagickWand/

# Quick and partial example

Since this is a CGO binding, Go GC does not manage memory allocated by the C API then is necessary to use Terminate() and Destroy() methods.

```go
package main

import "github.com/gographics/imagick/imagick"

func main() {
	imagick.Initialize()
	defer imagick.Terminate()

	mw := imagick.NewMagickWand()
	defer mw.Destroy()

	...
}
```

### License

[MIT](https://github.com/GroundSix/imagick/blob/master/LICENSE)
