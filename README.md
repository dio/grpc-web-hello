# Simple greeter grpc-web service

```
$ docker-compose up -d
$ # Open browser, point to: localhost:8000, or
$ curl 'http://localhost:8080/helloworld.Greeter/SayHello' \
  -H 'Accept: application/grpc-web-text' \
  -H 'X-User-Agent: grpc-web-javascript/0.1' \
  -H 'X-Grpc-Web: 1' \
  -H 'Content-Type: application/grpc-web-text' \
  -H 'Origin: http://localhost:8000' \
  --data-binary 'AAAAAAcKBVdvcmxk' \
  --compressed \
  --verbose
```
