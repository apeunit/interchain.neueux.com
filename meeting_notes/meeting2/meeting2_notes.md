---
title: Full Notes
parent: 2. Meeting, Nov 13 2020
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# **Second Meeting: Friday, November 13⋅2:00 – 3:00pm UTC**

- [https://github.com/ChainAgnostic/CAIPs/issues/27](https://github.com/ChainAgnostic/CAIPs/issues/27)

## Discoverability

- Yahoo
- DNS
- Search Engines

## Relayer is similar to discoverability service

- API in a relayer that allows whoever to query the relayer to query all chains it’s attached to
- [https://github.com/cosmos/relayer/pull/323](https://github.com/cosmos/relayer/pull/323)

## Naming Chain?

- Peer discovery looking for RPC endpoints?

## Ease of use

### Relayer that allows querying many chains at once

- Very doable
- Blocker is finding RPC endpoints that is reliable for each of those chains
- The logical service that is running all of these
    - Gets expensive quickly but with funding could set up for a year or two

### Centralized version of name chain

- Github registry
    - Example: https://github.com/ethereum-lists/chains
- Code owners / roles for repos
- Bot that easily updates the information
    - RPC that queries against all that it knows as well as pulling net info for
- RPC crawler from bez

### Name Chain

- Some sort of oracle like properties for RPC endpoings
- Continually update headers for these chains
- DNS chain
- Disambiguating human readable chains
- Token Curated Registries

## Data Provider

- Data hub
- Infura
- For cosmos
    - What’s an easy way to pay for data provider access
    - This service exists
        - [Pocket network](https://www.pokt.network/)

## Uniswap’s token list

- [Token List](https://tokenlists.org/)

## In Cosmos we need chain-ids

- Not token lists

## Denis

- People will create different solutions
- Whichever works will get critical mass
- Chains start from starport network, DNS for chain ids
- A chain is identified by an ID
- Better not to make a standard that everyone will follow
- Is it a goal of starport to become a chain naming service?
    - For the chains launching form starport network yes
    - It would naturally align itself to be the go to chain id name service
    - Register upgrades and genesis files here

## Github idea again

- It was a failure because it was more important for wallets to worry about asset ids rather than chain ids
- The need may be back though
- Need to access node IP address
- When tey started, they realized what was most important was asset ID
- P2P identifiers versys RPC identifiers
    - Slightly susceptible to DDOS so most people don’t make them public
- Roots of trust for stake sync
- Genesis files
- Chain ids
- ICF most trustworthy host
- Cosmos most views

## Seed Nodes as a service

- What exists for ethereum or btc
- Hard coded in the clients

## Github list

- What’s the risk?
- What’s the vulnerability?
- We don’t want infura because we can’t unseat it
    - Centralized points of failure because people start leaning on them
- 6 month project with a 2 person team?
- Chain starter / DID module
- No one needs to run the nodes, just a service that queries the RPC for peers, genesis file and roots of trust for the light client and regularly updates the repo (via CI)
    - Requires at least one open RPC endpoint
- Each chain project that exists should want to list their chain on this service
- If we make the burden of running minimalist, otherwise as a validator i’m happy to run a daemon on one of my sentry nodes and provide the info for the networks i validate on

## Brian

- Validators could keep running this, why not include it in the relayer itself?
- Relayer that connects to intermediary chains, lists all endpoints available for that chain, each validator of that network is already connected to that relayer
- When the relayer bootstraps it requires a bootstrap root of trust for the light client
- Relayer is pulling it from naked RPC endpoint

## Josh

- Native support on keplr, need this info on the repo and they will support it natively

## Provider list

- How to authenticate the provider
- How to rank the provider?
- RPC endpoints is a DDOS threat
    - They’re secured through anonymity
    - Initial goal maybe isn’t the RPC, build to that
    - Initially, peers, genesis and light client roots of trust allow anyone to build a new node trustworthy
    - Would allow bringing new nodes online very quickly

## Data will change

- Should we use a chain-id as the identifier?
- Yes
- Then you don’t need to worry about who is the “true” chain
- Wallets want to know who is the “true” chain

## This is just a building block

- A relayer that can use this repo can provide other future services regarding the asset denominations and IBC