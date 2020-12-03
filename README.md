# ut2004
A dedicated Unreal Tournament 2004 server

[![Docker Pulls](https://img.shields.io/docker/pulls/reflectivecode/ut2004.svg)](https://hub.docker.com/r/reflectivecode/ut2004/)

## Quickstart

This sample starts a CTF match and enables the web interface at http://localhost/ with admin password password1234

```
docker build -t debian:ut2004

docker run -d \
    --name ut2004 \
    --entrypoint "/bin/bash"
    -p 80:8080 \
    -p 7777:7777/udp \
    -p 7778:7778/udp \
    -e "CONFIG_1=[Engine.AccessControl];AdminPassword=password123;[UWeb.WebServer];bEnabled=True;ListenPort=8080" \
    -e "UT2004_CMD=CTF-FACECLASSIC?game=XGame.xCTFGame" \
    debian/ut2004

# not needer anymore?
docker exec -it ut2004 bash
# apt update
# apt install nano
# nano /usr/local/bin/config.sh
# "Add mkdir"
# /usr/local/bin/config.sh
# /usr/local/bin/run-user.sh
```



## Features

* Full-patched 64-bit dedicated server
* Support for downloading and installing addons (maps, mutators, etc)
* Support for configuring advanced ini settings
* Support for compressing addons for serving via nginx, apache, etc
* Support for web interface
