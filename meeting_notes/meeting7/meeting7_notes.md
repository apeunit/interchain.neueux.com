---
title: Full Notes
parent: 7. Meeting, Feb 1 2021
grand_parent: Meeting Notes
has_children: false
nav_order: 1
---
# Seventh Meeting: Monday, Feb 1⋅3:00 – 4:00pm UTC, Focus Topic: Blockchain Explorers

## Welcome new members
* Mira from Map of Zones
* Rick from Vulcanize
	* working on Tendermint / Cosmso for a long time
	* Chain registry with Auctions

## Updates from other projects (12 mins)

### Chain working Group (Denis)
* first call was last week
* adding new chain ids
* mapping chain id and seednodes and correlating via IBC versus correlating via governance
* [GitHub Issue 100](https://github.com/tendermint/spn/pull/100)

### GitHub Registry
* testing access rights
* tmcrawl learnings
* plan to bring learings back to on-chain registry WG
* next steps is a tutorial

## Map of Zones
mapofzones.com
Mira presenting

### Where they're at now
* explorer of all the zones with an IBC connection with at least one zone
* only focus on IBC interactions between zones
* can only show one hub of tokens
* showing a single testnet right now (not a lot of activity)
* Map of Zones 4 node testnet
* some zones may only focus on outgoing transactions
* percentage of IBC transactions vcompared to total transactions
* TBD: What is most interesting to the user
* number of connections
* Outsider wants to see: Where can I send my tokens directly from one zone to another
    * I can see there are only 3 options, can use the map of zones to see options as well as paths to a far away zone. 
    * Click a spceific zone to reveal more of network topology

### Future Direction
* once multi-hop IBC transfers take place will be better informed
* making map 3d and with more data
* What additional metrics for a specific zone
* topology at large

### github.com/cosmos/registry
* what zones are online, what is their topology, where are the active relayers that one can use (do they do it automatically or not)
* No incentive at the moment to close channels, find out which relayers are active might be difficult
* Do we need a relayer registry?
* Denom might be missing

### Who is the primary user?
* token holder, intersted in looking at where they can hold / send tokens
* Mira: under active discussion, hard to predict
* They think right now to focus on the metrics, select one particular zone, more data and stats compared to other zones
* Where is it connected and where is the zone at?
* less information abuot standalond and more how it acts
* also to show new people in the ecosystem how active cosmos is
* network discovery
    * new zone i haven't heard of, i want to go and look at it

### initial use and values
* started as a hackatom project (hackatomV) then came  game of zones
    * wasn't an actual leader board
    * focus was on keeping the connection alive (needed to send a particular type of transaction that wasn't available to the user)
    * phase 2 and 3 were more relevant
        * the most amount of packets (that was a highlight for map of zones)
* increased expectations on how many zones could be there
* some people were blocking IPs so data wasn't correct, reaching out to those people to get a good relationship to track the RPC endpoing
* What can we do with that dry data and how to surface it to users who are less technical but interested in zones and interactions

### Do you see this more as a tool or as a future of how this could developer—for users to trade an asset back to the origin—or more as a tool for developers to better understand what is going on in the network
* less about token history (right now there isn't a clear desicn for multi-hop interactions)
    * not clear to track where the token came from
    * hard to figure out that the token went out successfully but failed to come into zone b
    * how do we surface that information to the user
    * tracking token transfers historically
* for developers
    * i'm a new zone, where do i need to be connected
    * other hubs available, or if my goal is to connect to 3 zones how do i get the best connection there
* for investors
    * want to see how "connected" that zone is
* tool to surface information that isn't otherwise available
* much easier to tell if a chain-id is legit from looking on map of zones compared to making all of the queries necessary to do the same

### Relayer group needed
* set up a relayer chat on discord or telegram and invite initial group + relevant wallets

### Recap & Takeaways (schedule topic specific talks, 10min)
* Interchain Accounts
    * Keplr / Interchain Berlin
* Updates from
    * Chain Registry / Auction
* Block Explorers
    * Confio / IBC Visualizer
        * https://github.com/CosmWasm/ibc-visualizer
* Asset registry (CASA / Antoine)