# bfchroma

![Go Version](https://img.shields.io/badge/go-1.8-brightgreen.svg)
![Go Version](https://img.shields.io/badge/go-1.9-brightgreen.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/Depado/bfchroma)](https://goreportcard.com/report/github.com/Depado/bfchroma) 
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/Depado/bfchroma/blob/master/LICENSE)

Integrating Chroma syntax highlighter as a blackfriday renderer

## Usage

```go
bfchroma.Renderer{
	Base: bf.NewHTMLRenderer(bf.HTMLRendererParameters{
		Flags: bf.CommonHTMLFlags,
	}),
	Style: "monokai",
}
```

## Example

```go
package main

import (
	"fmt"

	"github.com/Depado/bfchroma"

	bf "gopkg.in/russross/blackfriday.v2"
)

var md = "This is some sample code.\n\n```go\n" +
	`func main() {
fmt.Println("Hi")
}
` + "```"

func main() {
	r := bfchroma.Renderer{
		Base: bf.NewHTMLRenderer(bf.HTMLRendererParameters{
			Flags: bf.CommonHTMLFlags,
		}),
		Style: "monokai",
	}
	html := bf.Run([]byte(md), bf.WithRenderer(&r))
	fmt.Println(string(html))
}
```

## ToDo

- [ ] Add tests
- [ ] Add a function to set the theme
- [ ] Use directly `chroma.Style` in the structure
