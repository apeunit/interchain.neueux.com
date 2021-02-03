---
title: Full Notes
parent: 4. Meeting, Dec 7 2020
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# **Fourth Meeting: Monday, Dec 7⋅3:00 – 4:00pm UTC**

## ApeUnit Stewarding

- Neueux.com (tba)
- Reaching out to participants to collect emerging ux challenges

## Welcome New Faces

Andrew Chiw

- LaunchControlD for [Eventivize](https://eventivize.co/) / ApeUnit

Shaun Conway

- Leading ICS for NFT and Metadata with Persistence One
- [https://internft.org](https://internft.org/)
- Cosmos SDK project
- Ixo

James with ApeUnit

- Communications and marketing

## High level priorities

### Next steps on registry

- Concrete tasks
    - Cron
    - CODEOWNERS
    - `tm-crawl`
    - Create cosmos repos for further mgt
- Location
    - If in cosmos, can be automated to be included in chain agnostic registry
        - Recommended by Pedro (?)

### Separation of DevX and UX

- Emerging CosmJS working group as well as dev adoption working group

### [Discuss extensions ot CAIP 27](https://github.com/ChainAgnostic/CAIPs/issues/27)

- Contact Pedro and Fede to push this topic forward
- Multi-query seems to be the way to go

- Rick scenario
    - Imagine there’s a chain with a fork
    - Who knows what kind of node you need to be running in order to resolve that query
        - Full node? Light node?
    - Abstraction
        - Find what an origin is
            - Hash linked data structure in order to provide verification
        - Assume these all exist at a single endpoint
        - Example: Rick’s chain
            - It’s like iota (no provenance for all assets created)
                - Can’t access this system, needs to be a blockchain or a state channel (hash linked data structure)
            - If we have that structure and all the assets needed to link that hach linked data structure (assuming they all can do this)
            - We have a pool of all checkpoints we’d ever need within our registry
                - Can’t come in if there’s not someone providing checkpoints
                - This is the cron for keeping these in sync
                - Fine to use github as the initial solution
                - Needs more than the automation of a cron job doing this work
                - Find out where the Filecon work is on this topic
    - Question
        - If a denom is being renamed does it break everything?
        - IBC Question
            - Do denom changes cascade?
        - Chain ID is stored on the client side
            - Just needs the validator set

## Future topics / projects

Mintscan

- Multi chain Block explorer

ZTake

- Map of zones

Confio

- IBC visualizer

Filecoin

- Verifiable checkpoints

UCRegistry

- [https://github.com/UCRegistry/asset-directory/tree/main/assets](https://github.com/UCRegistry/asset-directory/tree/main/assets)

Starport

- Genesis coordination for onboarding validators

Chainapsis Keplr IBC findings

- Reach out to Josh
- Customer view would be helpful

CAIP - Deep Linking

- Trust Wallet, Starname (Antoine)

## New Members

- UX improvements on Tendermint