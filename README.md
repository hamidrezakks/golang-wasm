### Usage

Use the docker images `nlepage/golang_wasm` and `nlepage/golang_wasm:nginx` to build and run a Go program as WebAssembly binary.

Example `Dockerfile`:
```
FROM nlepage/golang_wasm AS builder

COPY ./ src/app/
RUN go build -o test.wasm app

FROM nlepage/golang_wasm:nginx

COPY --from=builder /go/test.wasm /usr/share/nginx/html/
```

Build and run then visit http://localhost:32XXX/wasm_exec.html

### Examples

Find out about the examples in [examples/](https://github.com/nlepage/golang-wasm/tree/master/examples) or use the image `nlepage/golang_wasm:exampes` to run theses with:

```sh
docker container run -dP nlepage/golang_wasm:examples

# Find out which host port is used
docker container ps
```

Visit http://localhost:32XXX/, and follow the links.
