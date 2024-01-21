# FTP Server

A simple FTP server, using
[`vsftpd`](https://security.appspot.com/vsftpd.html).

(This is a fork of https://github.com/garethflowers/docker-ftp-server with a few patches incorporated - I've tried to swap my handle in the bare minimum places necessary for clear independent builds and pushes to Dockerhub until those patches can be upstreamed)

## How to use this image

### start a FTP Server instance

To start a container, with data stored in `/data` on the host, use the
following:

```sh
docker run \
	--detach \
	--env FTP_PASS=123 \
	--env FTP_USER=user \
	--name my-ftp-server \
	--publish 20-21:20-21/tcp \
	--publish 40000-40009:40000-40009/tcp \
	--volume /data:/home/user \
	campadrenalin/ftp-server
```

### ... via `docker compose`

```yml
services:
  ftp-server:
    container_name: my-ftp-server
    environment:
      - FTP_PASS=123
      - FTP_USER=user
    image: campadrenalin/ftp-server
    ports:
      - '20-21:20-21/tcp'
      - '40000-40009:40000-40009/tcp'
    volumes:
      - '/data:/home/user'
```

## License

-   This image is released under the
    [MIT License](https://raw.githubusercontent.com/campadrenalin/docker-ftp-server/master/LICENSE).
