# GO Challenge

**Para rodar a imagem basta executar o comando abaixo:**

`docker run --rm franciscoprovete/go:prod`

**Para fazer pull da imagem basta executar o comando abaixo:**

`docker pull franciscoprovete/go:prod`


**Link do Docker Hub**

[Docker Hub](https://hub.docker.com/r/franciscoprovete/go)


Segue abaixo o conteúdo do arquivo **Dockerfile**

```
FROM golang:alpine AS builder

WORKDIR /app
COPY main.go .

RUN go build -ldflags="-s -w" main.go

FROM scratch

WORKDIR /app
COPY --from=builder /app/main .

ENTRYPOINT [ "./main" ]
```


Segue abaixo o conteúdo do arquivo **main.go**

```
package main

import "fmt"

func main() {
  fmt.Println("FullCycle Rocks!")
}
```

**OBS:** no vídeo Wesley fala para colocarmos "FullCycle Rocks" e no exercício está "Code.education Rocks!", fiz conforme o passado no vídeo... = )
