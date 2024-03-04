# Brace Network - Testnet

Brace Network Testnet - local development network for fork of the Ethereum network with proof-of-stake enabled (Beacon Merge) for the Brace Network
This configuration uses Prysm as a consensus client and go-ethereum for execution. It starts from proof-of-stake and does not go through the Ethereum merge.

This sets up a single node development network with 64 deterministically-generated validator keys to drive the creation of blocks in an Ethereum proof-of-stake chain. Here's how it works:

  1. We initialize a go-ethereum, proof-of-work development node from a genesis config
  2. We initialize a Prysm beacon chain, proof-of-stake development node from a genesis config

The Brace Testnet is fully functional and allows for the deployment of smart contracts and all the features that also come with the Prysm consensus client such as its rich set of APIs for retrieving data from the blockchain.

# Using

First, install Docker. Then, run:

```console
git clone https://github.com/D-H-O-R-A/brace-network-pos && cd brace-network-pos
./clean.sh
docker compose up -d
```

Each time you restart, you can wipe the old data using ./clean.sh.

Next, you can inspect the logs of the different services launched.

To check geth, use:

```console
docker logs brace-network-pos-geth-1 -f
```

To check validator details, use:

```console
docker logs brace-network-pos-validator-1 -f
```

To check Beacon chain details, use:

```console
docker logs brace-network-pos-beacon-chain-1 -f
```

# Available Features:

*The network launches with a (Validator Deposit Contract)[https://github.com/ethereum/consensus-specs/blob/dev/solidity_deposit_contract/deposit_contract.sol] deployed at address 0x4242424242424242424242424242424242424242. This can be used to onboard new validators into the network by depositing 32 ETH into the contract

# Details

*When adding the privateKey of the validator address in sk.json, don't forget to change the address that will receive the first Braces in the genesis file and change the address in docker-compose.yml.
