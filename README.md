# Simple greeter grpc-web service

```
$ docker-compose up -d
$ # Open browser, point to: https://ok.local:8000 (see Tips below), or
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
```

## Testing using browser

Visiting https://ok.local:8000 surely triggers: "This connection is not private" for Safari and `NET::ERR_CERT_INVALID` for Chrome.

For Safari you can force to visit the website. While in Chrome you can type the magic work: badidea
or thisisunsafe in the page.

![safari](https://user-images.githubusercontent.com/73152/87927676-c61a8080-caad-11ea-909a-3456a94ab9c9.png)

## Tips

Add `ok.local` entry in your `/etc/hosts`.

```
127.0.0.1        ok.local
```
