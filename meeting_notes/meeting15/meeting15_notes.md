---
title: Full Notes
parent: 15. Meeting, June 8 2021
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---

# 15th Meeting: Monday JUNE 8th 3:00 - 4:00pm UTC

## Updates:
 * Andrew to discuss latest on Registry

## Discussion 1:

Registry not just useful for verifying chain identity. It's also useful to bootstrap new nodes. Especially automated deployment of new nodes.

* version number, binary location, genesis may seem superfluous but are important if you want to run a node (nowhere else to get all this info in one place)
* maybe home directory is a bit much
* take everything from Sunny's tm-network json
* Denominations, fee denoms
* Faucet URLs (for testsnets)
* ETH TokenLists for Cosmos is needed too


## Discusssion 2: 

Best approaches for crawling the network, check if nodes are really active

* Some tools are already out built by the community
* Adam: relatively easy to get blacklisted by nodes on the P2P port
* 26656 is usually the only port exposed. security reasons
* 26657 usually not exposed because easily DoSed, but useful for any browser/webapp that needs to query stuff
* 9090 GRPC mostly used for backends querying nodes, but needs batched requests
* having a list of 5-6 publicly (i think he means all available ports?) available nodes really helps for ux.
* Sunny really wants batched RPC requests on 9090, similar to GraphQL would be super useful, since for osmosis a lot of requests are necessary.

## Future Topics:
 * Discuss what further items to include in the Registry (Sunny)