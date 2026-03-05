# Research: Bitcoin Fork Coordination

How Bitcoin proposes, signals, and activates protocol upgrades.

## Governance Model

Bitcoin uses **off-chain governance** — proposals are discussed on mailing lists, GitHub, forums, and social media. There is no on-chain voting mechanism. Coordination costs are high, and contentious changes can take years to resolve (or fail entirely).

## The BIP Process

**Bitcoin Improvement Proposals (BIPs)** are the formal mechanism for proposing changes. The process is documented in [BIP-0001](https://github.com/bitcoin/bips/blob/master/bip-0001.mediawiki).

- Anyone can submit a BIP
- BIPs are reviewed by the community and BIP editors
- Types include Standards Track (consensus changes), Informational, and Process
- A BIP being merged into the repository does not imply acceptance — it must be implemented and activated

## Activation Mechanisms

Bitcoin has iterated through several activation mechanisms, each addressing shortcomings of the previous one.

### BIP 9: Miner-Activated Soft Fork (MASF)

- A bit in the block version field is chosen for signaling
- Miners signal readiness by setting the bit in blocks they produce
- If **95%** of blocks in a 2,016-block retarget period signal support, the fork "locks in"
- After lock-in, activation occurs after one more retarget period (~2 weeks)
- If the threshold is not met within the signaling window, the proposal expires

**Problems:** The 95% threshold was meant as a safety check, not a vote, but miners used it as veto power. This blocked the SegWit upgrade for over a year despite broad community support.

### BIP 8: Improved Activation with Optional Flag Day

Proposed as a response to BIP 9's shortcomings:

- Adds a `lockinontimeout` parameter — if `true`, the fork activates at the timeout height regardless of miner signaling
- Uses block heights instead of timestamps for more predictable scheduling
- Adds `minimum_activation_height` to prevent premature activation

**Key parameters:**
- `startheight` — when signaling begins
- `timeoutheight` — when signaling ends
- `threshold` — minimum blocks per retarget period for lock-in
- `lockinontimeout` — whether to force activation at timeout

### BIP 148: User-Activated Soft Fork (UASF)

- Full nodes enforce the new rules starting on a specific date ("flag day")
- Bypasses miner signaling entirely — relies on the "economic majority" (exchanges, businesses, users)
- Used to pressure miners into signaling for SegWit in 2017

### Speedy Trial (Used for Taproot, 2021)

- Based on BIP 8 with `lockinontimeout=false`
- Short signaling window (~3 months) to quickly test miner readiness
- If miners signal, great; if not, the community can try a different activation method
- Taproot locked in with 90%+ signaling within the first signaling period

## Notable Fork History

| Fork | Year | Type | Mechanism | Outcome |
|------|------|------|-----------|---------|
| P2SH | 2012 | Soft fork | BIP 16, miner signaling | Activated successfully |
| SegWit | 2017 | Soft fork | BIP 9 + BIP 148 UASF pressure | Activated after extended drama |
| Bitcoin Cash | 2017 | Hard fork | Contentious split over block size | Created BCH — permanent chain split |
| Taproot | 2021 | Soft fork | Speedy Trial (BIP 8 variant) | Activated smoothly |

## Lessons for ETC

1. **Miner signaling is not a vote** — high thresholds can be weaponized as veto power. ETC's rough consensus model avoids this by not gating activation on a specific signaling threshold.

2. **Flag days provide certainty** — ETC's approach of selecting a specific activation block height is similar to a flag day, giving all stakeholders a clear deadline.

3. **Contentious forks split the network** — Bitcoin Cash demonstrated that a hard fork without consensus creates a permanent split. ETC's consensus-first approach is designed to prevent this.

4. **Communication matters** — the SegWit saga showed that even technically sound proposals can stall without clear communication and stakeholder alignment.

## Sources

- [BIP 9: Version bits with timeout and delay](https://river.com/learn/terms/b/bip-9-soft-fork-activation/)
- [BIP 8 specification](https://github.com/bitcoin/bips/blob/master/bip-0008.mediawiki)
- [Soft fork activation — Bitcoin Optech](https://bitcoinops.org/en/topics/soft-fork-activation/)
- [Understanding Bitcoin fork activation methods](https://www.bitstack-app.com/en/learn-bitcoin/understanding-bitcoin-fork-activation-methods)
- [Forks, Signaling, and Activation — Eric Lombrozo](https://medium.com/@elombrozo/forks-signaling-and-activation-d60b6abda49a)
