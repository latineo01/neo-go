<p align="center">
<img
    src="https://res.cloudinary.com/latineo/image/upload/c_thumb,w_200,g_face/v1546981349/logo2.png"
    width="125px"
  >
</p>

<h1 align="center">neo-go</h1>

<p align="center">
  <b>Go</b> Nodo y SDK para el <a href="https://neo.org">NEO</a> blockchain.
</p>


# Overview

En este projecto podras encontrar una version en español de las versiones originales de  C# [NEO project](https://github.com/neo-project).
un set completo de herramientas para el blockchain de NEO, incluyendo:

- consensus node
- [RPC node & client](https://github.com/CityOfZion/neo-go/tree/master/pkg/rpc/README.md)
- RPC client
- CLI tool
- Smart contract compiler
- NEO virtual machine

# Getting started

## Installation

Install dependencies.

`neo-go` uses [dep](https://github.com/golang/dep) as its dependency manager. After installing `deps` you can run:

```
make deps
```

## How to setup a node

### Docker

Each tagged build is built to docker hub and the `:latest` tag pointing at the latest tagged build.

By default the `CMD` is set to run a node on `testnet`, so to do this simply run:

```bash
 docker run -d --name neo-go -p 20332:20332 -p 20333:20333 cityofzion/neo-go
```

Which will start a node on `testnet` and expose the nodes port `20333` and `20332` for the `JSON-RPC` server.


### Building

Build the **neo-go** CLI:

```
make build
```

Quick start a NEO node on the private network. This requires the [neo-privatenet](https://hub.docker.com/r/cityofzion/neo-privatenet/) Docker image running on your machine.

```
make run
```

To run the binary directly:

```
./bin/neo-go node -seed 127.0.0.1:20333,127.0.0.1:20334
```

By default the node will run on the `private network`, to change his:

```
./bin/neo-go node --mainnet
```

Available network flags:
- `--mainnet, -m`
- `--privnet, -p`
- `--testnet, -t`

If you want in-depth customization for your node, there are `yaml` config files for each `network` available in the `config` directory. Those files are automaticly loaded, corresponding the provided `netmode` flag.

```yaml
ProtocolConfiguration:
  Magic: 56753
  AddressVersion: 23
  StandbyValidators:
  - 02b3622bf4017bdfe317c58aed5f4c753f206b7db896046fa7d774bbc4bf7f8dc2
  - 02103a7f7dd016558597f7960d27c516a4394fd968b9e65155eb4b013e4040406e
  - 03d90c07df63e690ce77912e10ab51acc944b66860237b608c4f8f8309e71ee699
  - 02a7bc55fe8684e0119768d104ba30795bdcc86619e864add26156723ed185cd62
  SeedList:
  - 127.0.0.1:20333
  - 127.0.0.1:20334
  - 127.0.0.1:20335
  - 127.0.0.1:20336
  SystemFee:
    EnrollmentTransaction: 1000
    IssueTransaction: 500
    PublishTransaction: 500
    RegisterTransaction: 10000

ApplicationConfiguration:
  DataDirectoryPath: "./chains/privnet"
  RPCPort: 20332
  NodePort: 20333
  Relay: true
  DialTimeout: 3
  ProtoTickInterval: 2
  MaxPeers: 50
```

## Writing smart contracts in Go
Golang's development is been moved to a separate repository which you can find here [neo-storm](https://github.com/CityOfZion/neo-storm) 

# Contributing

Feel free to contribute to this project after reading the
[contributing guidelines](https://github.com/CityOfZion/neo-go/blob/master/CONTRIBUTING.md).

Before starting to work on a certain topic, create an new issue first,
describing the feauture/topic you are going to implement.

# Contact

- [@anthdm](https://github.com/anthdm) on Github
- [@anthdm](https://twitter.com/anthdm) on Twitter
- Reach out to me on the [NEO Discord](https://discordapp.com/invite/R8v48YA) channel
- Send me an email anthony@cityofzion.io

# License

- Open-source [MIT](https://github.com/CityOfZion/neo-go/blob/master/LICENCE.md)
