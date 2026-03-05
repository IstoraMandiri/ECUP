# Research: Tezos Fork Coordination

How Tezos handles protocol upgrades through on-chain self-amendment, avoiding hard forks by design.

## Governance Model

Tezos was explicitly designed to solve the "hard fork problem." Its protocol includes a built-in **on-chain governance and self-amendment mechanism** that allows the network to upgrade without requiring node operators to manually install new software.

This is fundamentally different from Bitcoin, Ethereum, and ETC, where hard forks require every participant to upgrade or risk being left on an orphaned chain.

## Self-Amendment Process

Tezos upgrades follow a structured, on-chain five-phase process. Each phase lasts approximately 2 weeks (~5 cycles), making the total process roughly **2.5 months**.

### Phase 1: Proposal Period

- Bakers (Tezos's equivalent of validators/miners) submit protocol upgrade proposals on-chain
- Multiple proposals can be submitted simultaneously
- Bakers vote for their preferred proposal
- The proposal with the most votes (above a minimum quorum) advances

### Phase 2: Exploration Vote

- Bakers vote Yes, No, or Pass on the leading proposal
- Requires a **supermajority (80%)** of non-Pass votes to be "Yes"
- Also requires minimum participation (quorum)
- If the threshold is not met, the proposal is rejected

### Phase 3: Cooldown Period

- A waiting period for the community to review and discuss the proposal further
- No voting occurs — purely for deliberation and testing

### Phase 4: Promotion Vote

- A second supermajority vote (same 80% threshold)
- Confirms the community still supports the proposal after the cooldown
- Acts as a safeguard against hasty decisions

### Phase 5: Adoption

- If the promotion vote passes, the new protocol is automatically activated
- Nodes self-update — no manual software upgrade required
- The old protocol is replaced seamlessly

## Key Design Principles

- **No hard forks needed** — the self-amendment mechanism is baked into the protocol
- **Baker-driven governance** — bakers (who stake Tez) are the primary voters
- **Supermajority required** — 80% threshold prevents contentious upgrades
- **Two-vote system** — exploration + promotion votes ensure sustained support
- **Cooldown period** — forced deliberation between votes reduces impulsive decisions
- **Invoice system** — proposal authors can include an "invoice" requesting compensation from the protocol, funded by inflation

## Notable Upgrades

Tezos has successfully executed numerous protocol upgrades through self-amendment:

| Upgrade | Date | Key Changes |
|---------|------|-------------|
| Athens | 2019 | First self-amendment — increased gas limit, reduced roll size |
| Babylon | 2019 | New consensus algorithm variant |
| Carthage | 2020 | Gas limit increase, bug fixes |
| Edo | 2021 | Sapling privacy features, tickets |
| Florence | 2021 | Increased operation size limit |
| Granada | 2021 | Liquidity baking, reduced gas costs |
| Hangzhou | 2021 | Timelock encryption, caching |
| Ithaca | 2022 | Tenderbake consensus (deterministic finality) |
| Jakarta | 2022 | Transaction rollups, ticketer |
| Kathmandu | 2022 | Pipelining, increased throughput |
| Lima | 2022 | Improved consensus, ghostnet |
| Mumbai | 2023 | Smart rollups, increased TPS |
| Nairobi | 2023 | Further rollup improvements |
| Oxford | 2023 | Adaptive issuance, staking |
| Paris | 2024 | Data availability layer |

## Lessons for ETC

1. **Self-amendment eliminates upgrade coordination pain** — Tezos never has to worry about nodes not upgrading, exchanges pausing, or chain splits. This is the gold standard for smooth upgrades, but requires the mechanism to be built into the base protocol.

2. **Not applicable to ETC without fundamental redesign** — ETC would need to redesign its core protocol to support self-amendment. This is not practical and would conflict with ETC's minimalist approach.

3. **The supermajority threshold (80%) prevents contention** — a high bar ensures broad agreement. ETC's rough consensus model aims for a similar outcome through social process rather than protocol enforcement.

4. **Two-vote system is a good pattern** — even in an off-chain process, ETC could adopt a "check-in" step between initial agreement and final activation (similar to the Go/No-Go decision in the activation checklist).

5. **Rapid upgrade cadence** — Tezos upgrades every few months, much faster than most blockchains. The self-amendment mechanism makes this low-risk. ETC's manual process means upgrades should be less frequent and more carefully coordinated.

6. **Trade-offs exist** — Tezos's smooth upgrades come at the cost of complexity in the base protocol and concentration of governance power in bakers. ETC's simpler approach is more aligned with its PoW and decentralization values.

## Sources

- [Tezos Protocol: Change and Evolution — Tezos Developer Portal](https://tezos.b9lab.com/blockchain-fundamentals/getting-2/)
- [Report on Blockchain Governance Dynamics — Project Liberty](https://www.projectliberty.io/wp-content/uploads/2024/07/Submitted-to-PL-Report-on-Blockchain-Governance-Dynamics.pdf)
- [Hard vs. Soft Forks — Fidelity Digital Assets](https://www.fidelitydigitalassets.com/research-and-insights/hard-vs-soft-forks-what-institutional-investors-should-know)
