# Research: Ethereum Fork Coordination

How Ethereum proposes, coordinates, and activates protocol upgrades.

## Governance Model

Ethereum uses **off-chain governance** centered around the **All Core Developers (ACD)** call — a biweekly video meeting where client teams, researchers, and community members discuss protocol changes. The EIP process provides the formal proposal mechanism, but ACD calls are where implementation decisions are made.

There is no on-chain voting. Since Ethereum's transition to proof of stake (The Merge, 2022), validators replace miners as the primary network participants who must upgrade software.

## The EIP Process

**Ethereum Improvement Proposals (EIPs)** are documented at [eips.ethereum.org](https://eips.ethereum.org).

- Anyone can submit an EIP via GitHub PR
- EIP editors review for formatting and completeness
- Types: Standards Track (Core, Networking, Interface, ERC), Meta, Informational
- Core EIPs (consensus changes) require inclusion in a network upgrade to take effect

### EIP Lifecycle

1. **Draft** — initial submission
2. **Review** — open for community review
3. **Last Call** — final review period (minimum 14 days)
4. **Final** — accepted and implemented

## Upgrade Coordination Process

Ethereum bundles multiple EIPs into named network upgrades (e.g., London, Shanghai, Dencun). The coordination process:

1. **EIP Champions** propose individual changes
2. **ACD calls** discuss which EIPs to include in the next upgrade
3. **Client teams** implement the EIPs in parallel
4. **Devnets** — short-lived test networks validate cross-client compatibility
5. **Public testnets** (Goerli, Sepolia, Holesky) — forks activated on testnets first, sequentially
6. **Mainnet activation** — a specific slot (post-Merge) or block number is chosen
7. **Post-fork monitoring** — client teams and the community monitor for issues

### Key Roles

- **EIP Champions** — propose and shepherd individual EIPs
- **ACD Call Facilitators** — coordinate the biweekly calls (historically Tim Beiko)
- **Client Teams** — Geth, Nethermind, Besu, Erigon, Lighthouse, Prysm, Teku, Lodestar, Nimbus
- **Ethereum Foundation** — funds research and development, but does not have unilateral authority
- **Testing Teams** — maintain test suites and devnet infrastructure

## Notable Fork History

| Fork | Year | EIPs | Notable Changes |
|------|------|------|-----------------|
| Homestead | 2016 | 2, 7, 8 | EVM improvements |
| DAO Fork | 2016 | — | State modification to recover DAO funds (created ETC) |
| Byzantium | 2017 | 9 EIPs | Precompiles, difficulty bomb delay |
| Constantinople | 2019 | 5 EIPs | Gas cost reductions, CREATE2 |
| Istanbul | 2019 | 6 EIPs | Gas repricing, new precompiles |
| Berlin | 2021 | 4 EIPs | Gas cost changes (EIP-2929, 2930) |
| London | 2021 | 5 EIPs | EIP-1559 fee market, difficulty bomb delay |
| The Merge | 2022 | — | Transition from PoW to PoS |
| Shanghai | 2023 | 5 EIPs | Validator withdrawals (EIP-4895) |
| Dencun | 2024 | 9 EIPs | Proto-danksharding (EIP-4844) |

## Lessons for ETC

1. **Bundled upgrades work well** — grouping multiple ECIPs into a single fork reduces coordination overhead and upgrade fatigue for node operators.

2. **Sequential testnet rollout** — activating on testnets one at a time (rather than all at once) catches issues early with lower stakes.

3. **Regular cadence** — Ethereum aims for roughly annual upgrades, giving stakeholders predictability. ETC could benefit from a similar rhythm.

4. **Cross-client testing is essential** — Ethereum's devnet process catches compatibility issues before testnets. With fewer clients, ETC has less risk here but should still test thoroughly.

5. **The DAO Fork is the cautionary tale** — Ethereum's willingness to modify state created ETC. This event is foundational to ETC's identity and reinforces why Code is Law matters.

6. **EIP-1559 partial adoption** — ETC's Mystique upgrade adopted only 2 of 5 London EIPs, showing that ETC can selectively adopt Ethereum changes that align with its values.

## Sources

- [Ethereum Classic — Wikipedia](https://en.wikipedia.org/wiki/Ethereum_Classic)
- [Protocol Upgrades — Ethereum Classic](https://ethereumclassic.org/knowledge/forks/)
- [Ethereum Fork History — Ethereumbook](https://cypherpunks-core.github.io/ethereumbook/appdx-forks-history.html)
- [Hard vs. Soft Forks — Fidelity Digital Assets](https://www.fidelitydigitalassets.com/research-and-insights/hard-vs-soft-forks-what-institutional-investors-should-know)
