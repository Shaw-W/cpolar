# cpolar

[![cpolar](http://dockeri.co/image/razerx/cpolar)](https://hub.docker.com/r/razerx/cpolar)

Docker Image packaging for cpolar. (amd64, arm32v6, arm32v7, arm64v8)

### > [官网](https://www.cpolar.com) | [官方文档](https://www.cpolar.com/docs) <

## Usage

- docker cli

    ```bash
    docker run -d --name cpolar \
        -v /docker/config/cpolar:/cpolar \
        --restart always \
        --network host \
        razerx/cpolar
    ```

- docker-compose/stack

    ```yml
    version: '3.7'

    services:
    cpolar:
        container_name: cpolar
        image: razerx/cpolar
        volumes:
        - /docker/config/cpolar:/cpolar
        restart: always
        network_mode: host
    ```

## License

Apache 2.0
