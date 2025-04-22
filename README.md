# spacetele

A swiss-knife proxy powered by [SpaceDHT](https://github.com/samooth/spacedht)!

## Installation
```
npm install -g spacetele // spacedht server proxy
npm install -g space-cmd-utils // keygen utils
```

## Server

Standard pipe server

```sh
spacetele-server --help
```

**Create a JSON config file for your server**
```
{
  "seed": "SEED",
  "allow": [
    "CLIENT_PEER_KEY",
    ...
  ]
}
```

```
options:

-l PORT : port of the service you want to expose to the peers
--address ADDRESS : IP of the service you want to expose to the peers
--cert-skip : skip certificate check when connecting to the service
--seed SEED : seed (command-line)
--compress : enable chunk compression
--private : make the proxy private (do not leak the access capability to the DHT)
```

```sh
examples:

spacetele-server -l 22 -c config-server.json
spacetele-server -l 22 --seed XXX
```

Note: the command will print out the pubkey


## Pub

Pub server

```sh
spacetele-pub --help
```

**Create a JSON config file for your server**
```
{
  "seed": "SEED",
  "allow": [
    "CLIENT_PEER_KEY",
    ...
  ]
}
```

```
options:

-l PORT : port of the service you want to expose to the peers
--address ADDRESS : IP of the service you want to expose to the peers
--seed SEED : seed (command-line)
--compress : enable chunk compression
```

```sh
examples:

spacetele-pub -l 5555 -c config-server.json
spacetele-pub -l 5555 --seed XXX
```

Note: the command will print out the pubkey


## Client

```sh
spacetele --help
```

**Create a JSON config file for your client**
```
{
  "peer": "SERVER_PEER_KEY"
}
```

```
options:

-s SERVER_PEER_KEY : server peer key (command-line)
-i keypair.json : keypair file
--compress : enable chunk compression
--private : access a private spacetele server (expects -s to contain the server's seed instead of the public key)
```

Read more about using identities here: https://github.com/prdn/space-cmd-docs/blob/main/identity.md

```sh
examples:

spacetele -p 1337 -c config-client.json
spacetele -p 1337 -s PUBKEY_FROM_SERVER -i keypair.json

and...
telnet localhost 1337
```

## The space-cmd system

spacetele supports the space-cmd system!

Identity management: https://github.com/prdn/space-cmd-docs/blob/main/identity.md

Host resolution: https://github.com/prdn/space-cmd-docs/blob/main/resolve.md

## License

MIT
