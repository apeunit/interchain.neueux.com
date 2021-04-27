---
title: The Challenges of Multichain Assets: an Introduction
parent: Blog Posts
has_children: false
nav_order: 1
---


# The Challenges of Multichain Assets: an Introduction
Cosmos’ grand vision is an [»Internet of Blockchains«](https://cosmos.network/intro#designing-the-internet-of-blockchains) — a vast network of interconnected blockchains, or zones as they are called in the Cosmos ecosystem.

But why have multiple blockchains when one could have all applications on a single, general-purpose chain instead? After all, having multiple applications on a single chain makes it much easier for them to communicate and share data. One answer is competition over resources; applications on the same blockchain must compete for the limited resources the network has available, e.g., block space. Another answer is specialisation. Application specific blockchains—the opposite of general purpose blockchains—are designed for their specific applications and can therefore be optimized much better than any general platform. ([This document has some more arguments](https://github.com/cosmos/cosmos-sdk/blob/master/docs/intro/why-app-specific.md))

This is where [the Inter-Blockchain Communication (IBC) protocol](https://cosmos.network/ibc) becomes relevant, which allows multiple blockchains to communicate with each other. However, this flexibility introduces a slew of complexities that need to be dealt with. Imagine the seemingly simple task of tracking and transferring a token across multiple blockchains.

We can look at this from the view-point of four different kinds of participants:

1. infrastructure providers/operators
2. developers
3. designers
4. application users

## Infrastructure providers/operators 
The IBC protocol describes how to transfer arbitrary data between different blockchains. This process requires a new piece of infrastructure: a relayer, which transports data packets between a pair of blockchains.
 
Currently relayers are not incentivized, so the question is: who would want to run a relayer? For now, the answer seems to be proponents of a specific blockchain who see a potential benefit in connecting a particular pair together, despite having to pay for relaying transactions on both sides.

Even though one operator can manage many relayers, this introduces a non-trivial amount of infrastructure that needs to be maintained, consisting of:

* relayer nodes
* blockchain nodes that are part of the networks a relayer is trying to relay packets for

To run a relayer between every possible pairing of blockchains out there would be a complexity nightmare, which is why the Cosmos Hub (itself a blockchain) exists, as a hub through which most blockchains can transfer data between each other. One simply needs to run a relayer between a blockchain and the Cosmos Hub.

## Developers
Suppose a developer wants to create a wallet that allows its users to track their tokens and that these tokens can only exist on one blockchain. In such a case, it is relatively straightforward for the developer to set up a service to extract the needed information and display it to the users.

However, we want an internet of blockchains, and managing a wallet for every single blockchain is a huge hassle. 

So if the developer wants to make it possible for users to track their tokens across IBC enabled blockchains, they now need to solve some hard problems.
Currently there is no authoritative list of which blockchains are out there, and how to reach the nodes of these blockchains, that the wallet can use to verify the provenance of tokens received via IBC.

A rudimentary example of such a service, for chains which are compatible with the Ethereum VM, is [chainlist.org](https://chainlist.org/). Users still need to manually interact with this website to discover the different chains but it is a step in the right direction.

An even better solution would be a service, from which a wallet can get all this information automatically. This is the approach [github.com/cosmos/registry](https://github.com/cosmos/registry) is trying to take - it is a semi-decentralized solution in that anyone can update the repository, but it is hosted on a centralized service: Github. There is talk of running a blockchain dedicated to this service (couldn’t it be a Cosmos SDK module?).

## Designers
If our developer friend successfully made the wallet able to track tokens across multiple blockchains, now a designer has the non-trivial task of making all this information legible to users. 

Assume we have an asset APE token, which a user holds on chain A and chain B. How does one display these balances in a way that makes sense to users and prevents them from making mistakes? One such mistake might be: the user wants to send APE tokens to an account on chain A but accidentally selects his APE tokens on chain B, which are then sent on the wrong chain.

## Application users
Now, if all of the previous actors do an excellent job of managing their new challenges, the user is presented with an easy-to-use wallet. Let us assume that they have 20 tokens on blockchain A and want to transfer those to blockchain B. If both of those zones (blockchains) have a direct connection, the user just needs an active relayer who can transfer their tokens - otherwise they will have to hope that the Cosmos Hub is already connected with both of these zones.

If there is no connection between the zones, direct or indirect, the user might be out of luck. In this case, they either have to wait for someone to set up a connection or find a centralized exchange/bridge to get their tokens where they want them to go.


## Conclusion
After reading this article, you should have a general idea of the different challenges introduced by multichain assets or IBC. If you prefer a more rigorous, technical dive into these topics, you can head over to [cosmos.network/ibc](https://cosmos.network/ibc) or [github.com/cosmos/ics](https://github.com/cosmos/ics) for all the nitty-gritty details.

Through collaborative, open dialogue, the Interchain Foundation’s UX working group works to build standards and applications that better user and developer experiences within the DLT space. To learn more about our work, explore our site. 

To participate in the UX Working Group, please join our [Telegram group](https://t.me/joinchat/E6CkGRrf0A_LswZeG0qvUg)!