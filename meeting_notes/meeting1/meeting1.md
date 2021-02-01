---
title: 1. Meeting, Oct 29 2020
parent: Meeting Notes
has_children: true
nav_order: 6
---

# 1. Meeting, Oct 29 2020

Reviewing existing [Chain Agnostic Improvement Proposals (CAIP)](https://github.com/ChainAgnostic/CAIPs) which touch on multi-chain assets.

- [CAIP-2](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-2.md) Blockchain ID Specification
    - when interacting with multiple different blockchains, each chain needs a unique identifier
    - the propoosed format has namespaces to be able to group chains which use the same naming standards
    - e.g. all cosmos chain identifiers start with `cosmos:`, `:` is the namespace separator
- [CAIP-5](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-5.md) Blockchain Reference for the Cosmos Namespace
    - specifies how names in the `cosmos` namespace should be formatted
- [CAIP-10](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-10.md) Account ID Specification
    - once a chain is uniquely identified, this standard governs how accounts on these chains are uniquely identified
- [CAIP-19](https://github.com/ChainAgnostic/CAIPs/blob/master/CAIPs/caip-19.md) Asset Type and Asset ID Specification
    - just like accounts, an asset needs also be uniquely identifiable on any given chain
    - Problem: this does not cover assets which move across multiple chains
    - once assets move, the path they take could be very relevant 
        - Discussion: add the path to the asset id?