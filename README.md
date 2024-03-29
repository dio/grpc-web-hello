# Simple greeter grpc-web, grpc-json transcoding service

```
$ # Optional, re-generating helloworld.bin needs Go 1.17.x. Note that we have the generated helloworld.bin already.
$ # Or you can install buf: https://docs.buf.build/installation/ on your system.
$ go run github.com/bufbuild/buf/cmd/buf@v0.54.1 build -o helloworld.bin
```

Running and testing the servers (frontend and backend, plus the Envoy front-proxy):

```
$ docker-compose up -d
$ # Open browser, point to: https://ok.local:8000 (see "Tips" section below), or
$ curl 'https://ok.local:8080/helloworld.Greeter/SayHello' \
  -H 'Accept: application/grpc-web-text' \
  -H 'X-User-Agent: grpc-web-javascript/0.1' \
  -H 'X-Grpc-Web: 1' \
  -H 'Content-Type: application/grpc-web-text' \
  -H 'Origin: http://localhost:8000' \
  --data-binary 'AAAAAAcKBVdvcmxk' \
  --compressed \
  --verbose \
  --insecure
$ # Calling the gRPC-JSON transcoding endpoint
$ curl 'https://ok.local:8081/say/hello' \
  -H "Content-Type: application/json" \
  -d '{"name": "Ok"}' \
  --compressed \
  --verbose \
  --insecure
```

## Testing using browser

Visiting https://ok.local:8000 surely triggers: "This connection is not private" for Safari and `NET::ERR_CERT_INVALID` for Chrome.

For Safari you can force to visit the website. While in Chrome you can type the magic word: badidea
or thisisunsafe in the page.

![safari](https://user-images.githubusercontent.com/73152/87927676-c61a8080-caad-11ea-909a-3456a94ab9c9.png)

## Tips

Add `ok.local` entry in your `/etc/hosts`.

```
127.0.0.1        ok.local
```

For testing if local reply works:

```
$ # Kill the backend, docker ps then docker kill <backend pid>
$ curl 'https://ok.local:8080/helloworld.Greeter/SayHello'
```
