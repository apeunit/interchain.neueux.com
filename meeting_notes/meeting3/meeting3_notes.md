---
title: Full Notes
parent: 3. Meeting, Nov 23 2020
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# **Third Meeting: Monday, November 23⋅3:00 – 4:00pm UTC**

## Status update on github discoverability progress

- [https://github.com/jackzampolin/registry](https://github.com/jackzampolin/registry)
- [https://github.com/jackzampolin/cosmos-registrar](https://github.com/jackzampolin/cosmos-registrar)

## New Questions

Priority: Give feedback!

TODO: Automating the checkpoints (cron)?

### What does it look like to build a node?

- Marko is a good person to ask about this
- Pass in bootstrap repository and chain id
    - Fill out config and fetch the genesis file
    - Could be automated
- Could at a minimum be a list of instructions
- Eventivize has something similar (We could tune, [https://github.com/apeunit/LaunchPayload](https://github.com/apeunit/LaunchPayload) and [https://github.com/apeunit/LaunchControlD](https://github.com/apeunit/LaunchControlD) to make it more universally useful)

### What does it look like to build a relayer with this information?

- RPC endpoints are needed for statesync
- In order to enable statesync you need to pass tendermint two RPC endpoints, anyone who wants to run a new node needs to run their own two nodes
- Small critical mass of RPC endpoints and create a culture of people building RPC endpoints
    - ICF?
    - AiB?
    - Chainapsis?
    - Some Validators
    - Chainlayer => Quicksync
        - Still takes ~12 hours
    - Forbole
    - Figment => [DataHub](https://figment.io/datahub/cosmos/)
    - Social pressure + small grants
        - Bounty program for uptime
        - Fixed amount distributed to nodes that are up
        - Automated polling
    - Statesync specific endpoint
        - Need RPC for light client
        - Why don’t we expose / integrate the light client into the P2P layer, then you don't need RPC for light client or state sync
        - Lean archival node
            - Only runs fast sync, always in fast sync mode, fetches new blocks and exposes RPC and only exposes data from the block store (commit, blockhashes) everything needed for a light client
            - DDoS vectors are still there
    - Minimal Viable Node
        - NGINX config
        - Cheapest plan possible
            - 4GB minimum
            - 2CPUs 8GB Ram
            - 500GB Disk
            - $80-$100/mo
                - GCP (Google Compute)
        - Enable State Sync
    - Easy to run solutions
        - EVENTEVIZE EZ Deploy
        - Validator package manager
    - Node service
        - Ping each node
            - 10 blocks from chain tip
            - 500ms latency
            - How much data is it holding
                - Pruning enabled?
        - Keep track of uptime
            - Rank and pay out top 10—100
    - Tm-crawler
        - Exposed ~45 endpoints
        - Begin just by showing the ones already open?
        - [TODO: integrate tm-crawler into github?](https://github.com/fissionlabsio/tmcrawl)
        - On atlas.cosmos.network?
- People need to regularly run these on cron
    - Find someone from each network to run

### TODO:

- CODEOWNERS enforcement
- chainlayer/quicksync — potential user

## [CAIP issue 27](https://github.com/ChainAgnostic/CAIPs/issues/27)

- Is it necessary to have a fully automated list of asset verification?
    - Alternatively you just limit views of assets you’ve personally verified
- Manual or Automated process will need to have access to all relative blockchain RPC endpoints
    - Alternatively it would have to be network by network via communication channels
- Query verification

### Use Case

- Resolving a chain id
- Resolving an asset
- Tied to each other
    - Once you’ve got the asset id you need the chain id
- User perspective
    - The dapp needs the RPC endpoints
- Who _should_ be running the RPC
    - Wallet doesn’t have capacity to be infrastructure for various networks
    - Best interest in applications to provide
    - Wallets can bridge these services

### Just saw Lunie sunset their infrastructure

- Can’t sustain running servers

### JS light client

- Still needs RPC endpoints

### Compensation for node operators

- Pay on delivery
- Pay for storage?
    - IPFS
- Eth land
    - Celo has something similar already

## Vulcanize

- Generic IPFS blockexplorer
- Convert blocks to IPLD blocks
- Blockchain specific block explorer based on top of that
- Generated IPLD data for Cosmos SDK apps