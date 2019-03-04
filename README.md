### smartcrop
---
https://github.com/muesli/smartcrop

```go
package main

import (
  "fmt"
  "image"
  _ "image/png"
  "os"
  
  "github.com/muesli/smartcrop"
  "github.com/muesli/smartcrop/nfnt"
)

func main() {
  f, _ := os.Open("image.png")
  img, _, _ := image.Decode(f)
  
  analyzer := smartcrop.NewAnalyzer(nfnt.NewDefaultResizer())
  topCrop, _ := analyzer.FindBestCrop(img, 250, 250)
  
  fmt.Printf("Top crop: %v+\n", topCrop)
  
  type SubImager interface {
    SubImage(r image.Rectangle) image.Image
  }
  croppedimg := img.(SubImager).SubImage(topCrop)
}
```

```
go get github.com/muesli/smartcrop

cd $GOPATH/src/github.com/mueli/smartcrop
go get -u -v
go build && go test -v
```

```
```


