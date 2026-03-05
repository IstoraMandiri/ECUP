# ECUP - Ethereum Classic Upgrade Process

> **Note:** This process is a draft proposal for consideration by the Ethereum Classic community. It has not been formally adopted and is open for discussion, feedback, and revision.

A formalised process for reaching consensus and executing hard forks on the Ethereum Classic (ETC) network.

## Purpose

Hard forks are a necessary mechanism for upgrading the Ethereum Classic protocol — fixing bugs, adding features, and maintaining compatibility where appropriate. However, ETC's origin as a response to the controversial DAO fork means the community holds an especially high bar for how forks are proposed, agreed upon, and executed. Pushing changes without consensus causes network splits.

This repository provides structured checklists, stakeholder mappings, and timelines to ensure that every hard fork follows a transparent, inclusive, and repeatable process rooted in rough consensus.

## How ETC Hard Forks Work

Ethereum Classic uses the [ECIP (Ethereum Classic Improvement Proposal)](https://github.com/ethereumproject/ECIPs) process to propose and coordinate protocol changes. The process is deliberately off-chain and permissionless — anyone can submit a proposal as a GitHub pull request. Proposals progress through stages (Draft, Last Call, Accepted, Final, Active) and require rough consensus from the community before client developers embed activation logic into release builds.

There is no on-chain voting. Consent ultimately rests with the network's users, miners, and node operators who choose which software to run.

## Repository Structure

```
fork-coordination/
├── README.md                 # This file — project overview
├── stakeholders.md           # Groups that must signal support or be notified
├── timelines.md              # Standard timeline and milestones for a fork
├── checklists/
│   ├── consensus.md          # Community consensus and signaling checklist
│   ├── implementation.md     # Client implementation and testing checklist
│   ├── activation.md         # Network activation and rollout checklist
│   └── post-fork.md          # Post-fork monitoring and incident response
└── research/
    ├── bitcoin.md            # How Bitcoin coordinates forks (BIPs, miner signaling)
    ├── ethereum.md           # How Ethereum coordinates forks (EIPs, ACD calls)
    ├── cardano.md            # How Cardano coordinates forks (CIPs, on-chain governance)
    └── tezos.md              # How Tezos coordinates forks (self-amendment)
```

## Checklists

Each fork should work through the following checklists in order:

| Phase | Checklist | Description |
|-------|-----------|-------------|
| 1 | [Consensus](checklists/consensus.md) | Build community support, collect stakeholder signals |
| 2 | [Implementation](checklists/implementation.md) | Implement in clients, test on devnets and testnets |
| 3 | [Activation](checklists/activation.md) | Set block height, release builds, coordinate upgrades |
| 4 | [Post-Fork](checklists/post-fork.md) | Monitor network health, handle incidents |

## Key Principles

- **Code is Law** — Hard forks must never override smart contract execution or modify application-layer state. ETC will never implement DAO-style bailout forks.
- **Rough Consensus** — No single party (developers, miners, or foundation) has unilateral authority. Broad agreement across stakeholders is required.
- **Proof of Work** — ETC is the largest smart contract platform secured by PoW. Fork coordination must account for miner economics and hashrate distribution.
- **Permissionless Participation** — Anyone can submit an ECIP, comment on proposals, or run a node. The process is open.

## Research

The `research/` folder documents how other blockchain networks handle fork governance, providing reference points and lessons learned:

- [Bitcoin](research/bitcoin.md) — BIP process, miner signaling (BIP 8/9), flag days
- [Ethereum](research/ethereum.md) — EIP process, All Core Devs calls, coordinated upgrades
- [Cardano](research/cardano.md) — CIP process, on-chain governance (CIP-1694), hard fork combinator
- [Tezos](research/tezos.md) — On-chain self-amendment, no hard forks by design

## Prior ETC Hard Forks

| Fork | ECIP | Block | Date | Purpose |
|------|------|-------|------|---------|
| Gotham | ECIP-1017 | 5,000,000 | Dec 2017 | Monetary policy — 210.7M ETC cap, 20% emission reduction per era |
| Atlantis | ECIP-1054 | 8,772,000 | Sep 2019 | Spurious Dragon + Byzantium compatibility |
| Agharta | ECIP-1056 | 9,573,000 | Jan 2020 | Constantinople + St. Petersburg compatibility |
| Phoenix | ECIP-1088 | 10,500,839 | Jun 2020 | Istanbul compatibility |
| Thanos | ECIP-1099 | 11,700,000 | Nov 2020 | DAG recalibration for 3GB miners (ETChash) |
| Magneto | ECIP-1103 | 13,189,133 | Jul 2021 | Berlin compatibility |
| Mystique | ECIP-1104 | 14,525,000 | Feb 2022 | Partial London compatibility (2 of 5 EIPs) |
| Spiral | ECIP-1109 | 19,250,000 | Jan 2024 | Shanghai compatibility |

## Contributing

This repository follows the same open contribution model as the ECIP process itself. To propose changes:

1. Fork this repository
2. Make your changes on a branch
3. Submit a pull request with a clear description
4. Engage in discussion and iterate

## License

This work is released under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) — no rights reserved.
