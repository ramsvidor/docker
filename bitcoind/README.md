# Debian based Bitcoin Core for Docker
[![](https://images.microbadger.com/badges/image/ramsvidor/bitcoind.svg)](https://microbadger.com/images/ramsvidor/bitcoind "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/ramsvidor/bitcoind.svg)](http://microbadger.com/images/ramsvidor/bitcoind "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/commit/ramsvidor/bitcoind.svg)](http://microbadger.com/images/ramsvidor/bitcoind "Get your own commit badge on microbadger.com")
[![](https://images.microbadger.com/badges/license/ramsvidor/bitcoind.svg)](http://microbadger.com/images/ramsvidor/bitcoind "Get your own license badge on microbadger.com")

Hands-on Docker image for Bitcoin Core development running on [Debian](https://www.debian.org).

This is a very minimalist container just for running testnet and develop on top of it. It cointains only the `bitcoind`
executable and should be queried from outside the container with `curl` or other similar tools.

Out-of-the-box, this image is configured to bind to all interfaces and default RPC authentication is 
`rpcuser=bitcoind` and `rpcpassword=secret`. **!!!DON'T RUN WITH THESE SETTINGS IN PRODUCTION!!!**

**@see** [Dockerfile](https://github.com/ramsvidor/docker/blob/master/bitcoind/Dockerfile)

## Base image
* [Official Debian 9 (Stretch)](https://hub.docker.com/_/debian) - stretch-slim variant.

## How to use this image
### Pull and start a Bitcoin Core daemon instance
* `docker pull ramsvidor/bitcoind`
* `docker run --name bitcoind ramsvidor/bitcoind`
* `docker run --name bitcoind -v data:/var/lib/bitcoind -v conf:/etc/bitcoind -p 18332:18332 ramsvidor/bitcoind`

Data is stored at `/var/lib/bitcoind` and configuration file is stored at `/etc/bitcoind`. You can use it with volumes.

## Supported Docker versions
This image is officially supported on Docker version 19.03 and newer.
Support for older versions is provided on a best-effort basis.
Please see the [Docker installation documentation](https://docs.docker.com/install/) for details on how to upgrade your 
Docker daemon.

## Contributing
You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull 
requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a 
[GitHub issue](https://github.com/ramsvidor/docker/issues), especially for more ambitious contributions. This 
gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you 
find out if someone else is working on the same thing.

## License
This code is open source software licensed under the [Apache 2.0 License]("http://www.apache.org/licenses/LICENSE-2.0.html").
