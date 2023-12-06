# perfsprint

[![CI](https://github.com/Lasiar/canonicalheader/actions/workflows/go.yml/badge.svg)](https://github.com/catenacyber/perfsprint/actions/workflows/ci.yml)

Golang linter for check canonical header.

### Example

before

```go
package main

import (
	"net/http"
)

const testHeader = "testHeader"

func main() {
	v := http.Header{}
	v.Get(testHeader)

	v.Get("Test-HEader")
	v.Set("Test-HEader", "value")
	v.Add("Test-HEader", "value")
	v.Del("Test-HEader")
	v.Values("Test-HEader")

	v.Set("Test-Header", "value")
	v.Add("Test-Header", "value")
	v.Del("Test-Header")
	v.Values("Test-Header")
}

```

after

```go
package main

import (
	"net/http"
)

const testHeader = "testHeader"

func main() {
	v := http.Header{}
	v.Get(testHeader)

	v.Get("Test-Header")
	v.Set("Test-Header", "value")
	v.Add("Test-Header", "value")
	v.Del("Test-Header")
	v.Values("Test-Header")

	v.Set("Test-Header", "value")
	v.Add("Test-Header", "value")
	v.Del("Test-Header")
	v.Values("Test-Header")
}

```