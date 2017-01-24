# ss-keepalive

Keepalive a shadowsocks service by trying to use it frequently.

## Usage

Run shadowsocks keepalive service:

    docker run -d --restart=always \
        -e SERVER_ADDR=<server> \
        -e SERVER_PORT=<port> \
        -e LOCAL_PORT=<localport> \
        -e PASSWORD=<password> \
        -e METHOD=<method> \
        -e TIMEOUT=<timeout> \
        -e TEST_URL=<url> \
        -e INTERVAL=<interval> \
        -e EXTRA_FLAGS=<...> \
        tydus/ss-keepalive:<version>

## Compose

Here is an example of docker-compose.yml:

```yaml
backend:
  image: tydus/ss-keepalive
  restart: always
  environment:
    - SERVER_ADDR=<server>    # default: 0.0.0.0
    - SERVER_PORT=<port>      # default: 8388
    - LOCAL_PORT=<port>       # default: 1080
    - PASSWORD=<password>     # default: <container-id>
    - METHOD=<method>         # default: aes-256-cfb
    - TIMEOUT=<timeout>       # default: 300
    - TEST_URL=<url>          # default: http://ifconfig.co
    - INTERVAL=<timeout>      # default: 3600
    - EXTRA_FLAGS=<...>       # "-v" for vervose log
```

## Build

    git clone https://github.com/Tydus/docker-ss-keepalive
    cd docker-ss-keepalive
    docker build -t ss-keepalive:latest

## License

(The MIT License)

