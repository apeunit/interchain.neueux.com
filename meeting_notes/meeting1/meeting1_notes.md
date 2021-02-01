---
title: Full Notes
parent: 1. Meeting, Oct 29 2020
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# First Meeting: Thursday, October 29

## Attending:

- Emil (ApeUnit), Dogemos (Chainapsis/Tendermint), Max (ApeUnit), Antoine (StarName), Dario (ApeUnit), Sasha (ApeUnit), Pedro (WalletConnect), Billy (ICF)

## Agenda:

### Intro

### Identify the problems

- IBC Coin Denoms
- Reliable Chain IDs
- Relaying IBC Packets
- Interacting with Multichains with Wallets

### We build interfaces around the technology

- It’s nice if we can build the technology around the user experience
- We all want to build our own applications for our own use cases but we also want to interface with each other with no conflict
- CAIPs began highly opinionated
- Universal Chain Registry
    - [https://tokenlists.org/](https://tokenlists.org/)
- CAIPs and DIDs have a self explanatory pattern
    - protocol: method: value
- Asset ID needs attention from this group
    - Resolution procedure
        - Put it into a client library?
        - Offers example as well as tool
        - Library should ask for a node provider tht can help resolve nodes?
    - CosmJS?
- IBC x identifies how to query a node for IBC info to identify the asset
    - If that asset query returns another CAIP19, if i have prior knowledge of that chain I will use it or i will revert to a registry

## Telegram [Invite](https://t.me/joinchat/E6CkGRrf0A_LswZeG0qvUg)

## Email invite

- Chainapsis (Tony & Josh)
- Lunie (Jordan & Fabo)
- Akash (Jack)
- Confio (Simon)
- WalletConnect (Pedro)
- ApeUnit (Emil, Max, Sascha)
- Agoric (Dean, …)
- 3box (Joel)
- Cosmostation/Stamper (David, …)
- Starname (Antoine)

## **Multi-chain Assets**

- Connected via IBC
    - Single Hop
    - Multi-Hop
    - Querying the path via IBC
        - gRPC
- Connected via Bridge
    - Eth
    - BTC
- Balancer
    - Should all similar origin assets be bundled in a balancer style basket per chain?

### [Chain Agnostic Improvement Proposals](https://github.com/ChainAgnostic/CAIPs)

### Info

- These are proposals for standards for storing chains and asset references for client libraries to maintain integrity (and sanity!) while tracking assets across multiple blockchains.

### **CAIP-2:** [Blockchain ID Specification](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-2.md)

- **Summary**: Chain ids should have a namespace (like eip155 which describes eth specific chain-ids, or bip122 which describes btc specific chain ids) and then a reference to a specific chain within that reference (like “1” for mainnet ethereum or “cosmoshub-3” for the current cosmos mainnet).
- **Examples**:
    - Ethereum mainnet
        - eip155:1
    - Bitcoin mainnet
        - bip122:000000000019d6689c085ae165831e93
    - Litecoin
        - bip122:12a765e31ffd4059bada1e25190f6e98
    - Cosmos Hub (Tendermint + Cosmos SDK)
        - cosmos:cosmoshub-2
        - cosmos:cosmoshub-3
    - Binance chain (Tendermint + Cosmos SDK; see https://dataseed5.defibit.io/genesis)
        - cosmos:Binance-Chain-Tigris
    - IOV Mainnet (Tendermint + weave)
        - cosmos:iov-mainnet

### **CAIP-5:** [Blockchain Reference for the Cosmos Namespace](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-5.md)

- Summary: chain-id for cosmos chains should follow regex [-a-zA-Z0-9]{1,47} and if not they should be hashed like: first_16_chars(hex(sha256(utf8(chain_id)))) and prefixed with “x”, “hash” or “hashed”
- Issue:
    - **Currently IBC based denoms breaks this spec**
- Examples:
    - Cosmos Hub (Tendermint + Cosmos SDK)
        - cosmos:cosmoshub-2
        - cosmos:cosmoshub-3
    - Binance chain
        - cosmos:Binance-Chain-Tigris
    - IOV Mainnet (Tendermint + Weave)
        - cosmos:iov-mainnet
    - chain_ids "x", "hash-", "hashed" (are direct)
        - cosmos:x
        - cosmos:hash-
        - cosmos:hashed
    - chain_ids "hashed-", "hashed-123" (invalid prefix for the direct definition)
        - cosmos:hashed-c904589232422def
        - cosmos:hashed-99df5cd68192b33e
    - chain_id "123456789012345678901234567890123456789012345678" (too long for the direct definition)
        - cosmos:hashed-0204c92a0388779d
    - chain_ids " ", "wonderland🧝‍♂️" (invalid character for the direct definition)
        - cosmos:hashed-36a9e7f1c95b82ff
        - cosmos:hashed-843d2fc87f40eeb9

### **CAIP-10:** [Account ID Specification](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-10.md)

- Summary
    - An account is only relevant to the chain on which it exists so it should be packaged together like account_id: account_address + "@" + chain_id
- Examples
    - Ethereum mainnet
        - 0xab16a96d359ec26a11e2c2b3d8f8b8942d5bfcdb@eip155:1
    - Bitcoin mainnet
        - 128Lkh3S7CkDTBZ8W7BbpsN3YYizJMp8p6@bip122:000000000019d6689c085ae165831e93
    - Cosmos Hub
        - cosmos1t2uflqwqe0fsj0shcfkrvpukewcw40yjj6hdc0@cosmos:cosmoshub-3
    - Kusama network
        - 5hmuyxw9xdgbpptgypokw4thfyoe3ryenebr381z9iaegmfy@polkadot:b0a8d493285c2df73290dfb7e61f870f
    - Dummy max length (63+1+16+1+47 = 128 chars/bytes)
        - bd57219062044ed77c7e5b865339a6d727309c548763141f11e26e9242bbd34@max-namespace-16:xip3343-8c3444cf8970a9e41a706fab93e7a6c4-xxxyyy

### **CAIP-19:** [Asset Type and Asset ID Specification](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-19.md)

- Summary
    - An asset has a specific origin which is referenced with the Blockchain ID specification, but within that setting there are various ways to designate a token. One way is slip44 where an asset number is registered. Another way is as an ERC-20 on EVM chains with a reference to a contract address. There is also the possibility that an asset has an ID on top for non-fungible tokens, this should be appended should it be necessary.
- **Issues**
    - This doesn’t address an asset once it’s moved away from it’s origin chain. In the SDK the path is namespaced as part of the asset as seen in **[ADR001**: Coin Source Tracing](https://github.com/cosmos/cosmos-sdk/blob/master/docs/architecture/adr-001-coin-source-tracing.md).
- Example:
    - Ether Token
        - eip155:1/slip44:60
    - Bitcoin Token
        - bip122:000000000019d6689c085ae165831e93/slip44:0
    - ATOM Token
        - cosmos:cosmoshub-3/slip44:118
    - Litecoin Token
        - bip122:12a765e31ffd4059bada1e25190f6e98/slip44:2
    - Binance Token
        - cosmos:Binance-Chain-Tigris/slip44:714
    - IOV Token
        - cosmos:iov-mainnet/slip44:234
    - Lisk Token
        - lip9:9ee11e9df416b18b/slip44:134
    - DAI Token
        - eip155:1/erc20:0x6b175474e89094c44da98b954eedeac495271d0f
    - CryptoKitties Collectible
        - eip155:1/erc721:0x06012c8cf97BEaD5deAe237070F9587f8E7A266d
    - CryptoKitties Collectible ID
        - eip155:1/erc721:0x06012c8cf97BEaD5deAe237070F9587f8E7A266d/771769

## **Proposals**

- Extend CAIP-19 to include IBC path information?
- Query a port and channel for the chain id like [here](https://github.com/cosmos/cosmos-sdk/blob/6e569e125571c6b0918ea97d1c7aa7384525eb2e/x/ibc/light-clients/07-tendermint/types/client_state.go#L28-L49)
- Denom would look like:
    - **ibcDenom = "ibc/" + hash(trace path + "/" + base denom)**
    - trace path = **{destPortN}/{destChannelN}/.../{destPort0}/{destChannel0}**
- **What does a user want?**
    - Blockchain : Denom
    - If it is IBC
        - Should have an asterisk?
        - Hover?
        - See the path it took as a popup showing the chain ids
        - Ability to debug shows the channel and port ids
    - View options
        - Group similar assets
            - All atoms grouped no matter what ibc path
            - All eth grouped no matter what bridge
            - All stable tokens grouped no matter what type?
- Standardization around slip44 paths within the ecosystem between wallets

## Asset Directory

- [https://github.com/iov-one/asset-directory](https://github.com/iov-one/asset-directory)
- Namespace on Tickers
- Namespace on CAIP-19s
- JS package to import into project for querying metadata
- API possible with Lambda function attached to github for most up to date endpoint

## Name Services

- Starname.me
    - Namespaced with an asterisk, stored on a cosmos sdk blockchain
    - Has a registry that includes slip44 addresses
    - Format is like: antoine*cosmos
- ENS
    - Following ICANN namespace (except for the .eth) in order to register data under human readable names.
    - Uses nested namespace so that TLD = .eth, .xyz currently with verification via DNS RSA signatures and soon to be all TLD addresses
    - Has a registry that includes slip44 addresses so a cosmos address can be stored like **cosmos.billyrennekamp.eth**
- [Subjective initialisation canonical name registry #483](https://github.com/cosmos/ics/issues/483)
    - Name service for chain IDs to be stored on chain
