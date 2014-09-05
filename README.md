docker-ufo-js
=============

This is a [docker](https://www.docker.com/) image intended to host a reproduction discussed in [***Introducing ufo.js: A browser-oriented p2p network,***](http://ieeexplore.ieee.org/xpl/login.jsp?tp=&arnumber=6785359&url=http%3A%2F%2Fieeexplore.ieee.org%2Fiel7%2F6778476%2F6785290%2F06785359.pdf%3Farnumber%3D6785359) (Bevilacqua, A; Boemio, P.; Romano, S.P. in *International Conference on Computing, Networking and Communications (ICNC), 2014* , pp.353,357, 3-6 Feb. 2014)

It sets up a simple container running ubuntu, node, and a [fork](https://github.com/coderigo/ufo.js-base) of the [original](https://github.com/TinyBoxDev/ufo.js-base) github repository, ready to go. The fork has some minor edits to make the application run with recent express versions.

## Installation

This was all set up on *OS X*, so it assumes you have followed the [docker OS X installation instructions](http://docs.docker.com/installation/mac/) and have run `boot2docker` from the command line and have the docker daemon running. If you're not on *OS X*, you'll just have to check that the docker daemon is running and it should all work.

To download the image and start a container from the image

```bash
docker pull coderigo/docker-ufo-js
# NOTE: The below command is designed for *OS X* running boot2docker which itself is a VM running on IP address 
# 192.168.59.103 by default (run boot2docker IP to see it for yourself). If running on other OSes you'll likely 
# substitute `192.168.59.103:49159` out for your localhost `127.0.0.1:9000`:
docker run -p 192.168.59.103:49159:9000 --name="ufo-js-server" --hostname="ufo-js-server" -i -t coderigo/docker-ufo-js /bin/zsh
```

The above will start an interactive shell into the container. To start the server, type into the shell:

```bash
cd ufo.js-base && ./bin/p2p
```

In the browser travel to `192.168.59.103:49159` (on OS X with boot2docker running) or `127.0.0.1:9000` on other OSes to load the `ufo.js` app.

## Contributing

This image can be changed at any time. To re-build simply:

`docker build --tag="docker-ufo-js" .`
