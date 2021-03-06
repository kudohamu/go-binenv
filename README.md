## Installation

```
$ go get -u github.com/jteeuwen/go-bindata/...
$ go get github.com/kazuph/go-binenv
```

## Usage

Set `.env`

```
$ cat .env
DATA="This is Data"
```

Run go-bindata

```
$ go-bindata .env
```

Access env data

```go
package main

import (
	"fmt"
	"github.com/kazuph/go-binenv"
)

func main() {
	env, err := binenv.Load(Asset)
	if err != nil {
		fmt.Println(err)
	}
	fmt.Printf("%#v\n", env)
	fmt.Printf("%s", env["DATA"])
}
```

Use multiple env files

```go
env, err := binenv.Load(Asset, ".env", "./foo/.env", "./bar/.env")
if err != nil {
	fmt.Println(err)
}
fmt.Printf("%#v\n", env)
fmt.Printf("%s", env["DATA"])

```
