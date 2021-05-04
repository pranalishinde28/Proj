# Steps
- Download Fabric Binaries
```
    curl -sSL https://bit.ly/2ysbOFE | bash -s -- 1.4.1 1.4.1 0.4.22 -d -s
```
- export binaries
```
    export PATH=${PWD}/bin:${PWD}:$PATH
```
- Generate crypto config
```
    cryptogen generate --config crypto-config.yaml
```
- Generate Genesis and channel block
```
    configtxgen -outputBlock channel-artifacts/genesis.block -channelID sys -profile FSCOrgsOrdererGenesis

    configtxgen -outputCreateChannelTx channel-artifacts/channel.tx -channelID supplychannel -profile FSCOrgsChannel
```
- Start Docker network
```
     docker-compose -f docker-compose-cli.yaml up -d
```