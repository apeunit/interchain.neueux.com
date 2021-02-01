---
title: Full Notes
parent: 5. Meeting, Dec 21 2020
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# **Fifth Meeting: Monday, Dec 21⋅3:00 – 4:00pm UTC**

## DNS for IBC

### Dennis

- Chain name service
- Tendermint Inc / Starport Cloud / Starport Network
- Interchan Conversations Demo
- Handy way to launch blockchains
    - Coordinate the creation of the genesis command
- Uses starport network ([github.com/tendermint/spn](https://github.com/tendermint/spn))
- Could store information about chains

### Could some chain information be on the Hub?

- Possible upstreaming of chain information SPN -> Hub
- Hub Minimalism
    - IBC enables scaling hub capabilities outside of the hub
    - Cross chain validation allows hub security
- SPN could have enough momentum to warrant be canonical location
- Disadvantage of having it on the hub?
    - Risky, doesn't allow fast iteration, might take a long time to get there and no guarantee
    - Cosmos vision includes many blockchains so putting every feature on one goes against that vision
- Pedro
    - Overhead of data on chain might as well be at a place of high discoverability, hub has strong network effects, hub denotes discoverability along with routing
- Denis
    - Using SPN is also a path towards the hub
    - Test new features on separate networks and aim towards hub after iterative approach
- Iteration
    - First github, then separate zone, then hub
    - Be wary of competing versions
- Context of Starname and Chain information
    - Focusing on people and organizations for human readable account address
    - Interested in getting asset id's configured properly
- Github solution could use redundancy
    - Radicle approach
    - Gitbackup
    - IPFS

## Update on the Registry

- [https://github.com/cosmos/registry](https://github.com/cosmos/registry)
- [https://github.com/cosmos/cosmos-registrar](https://github.com/cosmos/cosmos-registrar)
- Atlas
    - [https://atlas.cosmos.network](https://atlas.cosmos.network/)
    - Weighting endpoints
- RPC feature requests
    - Tendermit team is listening
- Module registry on github too?
    - Wants to know what modules are available on what chains
    - SDK would need some namespace ID for modules
    - Name spacing Msgs
        - Proto file
        - Relevant to Interchain Accounts
    - Define the function signatures of the modules
    - Introspection
        - [https://github.com/cosmos/cosmos-sdk/issues/4322](https://github.com/cosmos/cosmos-sdk/issues/4322)
        - [https://github.com/grpc/grpc/blob/master/src/proto/grpc/reflection/v1alpha/reflection.proto](https://github.com/grpc/grpc/blob/master/src/proto/grpc/reflection/v1alpha/reflection.proto)
        - [https://github.com/cosmos/cosmos-rust/issues/14](https://github.com/cosmos/cosmos-rust/issues/14)
        - Merged in: [https://github.com/cosmos/cosmos-sdk/pull/6463](https://github.com/cosmos/cosmos-sdk/pull/6463)
- Weights
    - App Block height
    - Response time
    - Timeout to be removed from query?
    - Could automatically add more networks depending on IBC connections
- Form
    - Clone and run tmcroawl
    - Outputs the json to Atlas to keep track of the json that was outputted
- Circle actions
    - Run each query in a separate go routine max timeout 100sec
- Initially valuable to eat those costs and ensure it's valuable at beginning
- What's the separation between github and atlas solutions?
    - 

## Map of Zones

- Mira Storm
- maps

## Messaging on wallets?

- Sunny wants to send a message to all delegators of his validator
- This is more of an interface question—would wallets want to start supporting the memo field better

## Chain Agnostic Standard Alliance

## Any working examples of cross chain contract call proxying system on top of IBC?