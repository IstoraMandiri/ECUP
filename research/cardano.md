# Research: Cardano Fork Coordination

How Cardano proposes, governs, and activates protocol upgrades.

## Governance Model

Cardano has transitioned to **on-chain governance** through CIP-1694 (the "Voltaire" era). This is the most structured governance model among major blockchains, with defined roles, voting thresholds, and constitutional constraints.

### Governance Bodies

1. **Constitutional Committee (CC)** — reviews governance actions for constitutional compliance. Acts as a check on proposals, not an originator of them.

2. **Delegate Representatives (DReps)** — ADA holders delegate their voting power to DReps, who vote on governance actions on their behalf. Any ADA holder can become a DRep.

3. **Stake Pool Operators (SPOs)** — validate transactions and produce blocks. SPOs vote on hard fork initiation specifically.

### Governance Actions

On-chain governance actions include:
- Hard fork initiation
- Protocol parameter changes
- Treasury withdrawals
- Constitutional amendments
- Motions of no confidence in the Constitutional Committee

## The CIP Process

**Cardano Improvement Proposals (CIPs)** are the off-chain proposal mechanism, similar to BIPs and EIPs. CIPs document technical specifications and are discussed on GitHub.

- CIPs are informational — they do not directly trigger on-chain governance
- On-chain governance actions reference CIPs but are submitted separately
- The Intersect member-based organization facilitates coordination

## Hard Fork Coordination: The Hard Fork Combinator

Cardano uses a unique mechanism called the **Hard Fork Combinator (HFC)** — a protocol-level feature that allows the network to transition between protocol eras without disruption.

### Activation Process

1. **CIP drafted and discussed** — technical specification published
2. **On-chain governance action submitted** — hard fork initiation proposed
3. **SPO vote** — at least 51% of SPOs must vote in favor (by upgrading nodes)
4. **DRep vote** — DReps vote on the governance action
5. **Constitutional Committee review** — CC confirms the action meets constitutional requirements
6. **Hard Fork Combinator activates** — protocol transitions seamlessly at a designated epoch boundary

### Recent Examples

**Chang Hard Fork (September 2024)**
- Initiated Cardano's on-chain governance era
- Established the Constitutional Committee, DRep, and SPO governance structure
- Required extensive community education and tooling development

**Plomin Hard Fork (2025)**
- Completed the governance transition
- Nearly 80% of SPOs upgraded (well above the 51% threshold)
- Constitutional Committee reviewed and approved
- Marked full activation of decentralized governance

## Voting Thresholds

| Governance Action | SPO Vote | DRep Vote | CC Approval |
|-------------------|----------|-----------|-------------|
| Hard fork initiation | 51% | 67% | Required |
| Protocol parameter changes | 51% | 67% | Required |
| Treasury withdrawal | — | 67% | Required |
| Constitutional amendment | — | 75% | Required |

## Lessons for ETC

1. **Formal roles reduce ambiguity** — Cardano's defined governance bodies make it clear who decides what. ETC's rough consensus model is more flexible but less predictable.

2. **On-chain voting creates accountability** — votes are transparent and auditable. ETC's off-chain process relies on social consensus, which is harder to measure.

3. **High coordination costs** — Cardano's governance system required years of development and significant community education. This level of formalization may be overkill for ETC's smaller ecosystem.

4. **The Hard Fork Combinator is elegant** — seamless era transitions reduce risk. ETC could study this approach for smoother upgrades, though it would require significant protocol changes.

5. **SPO threshold (51%) is pragmatic** — lower than Bitcoin's 95% miner signaling but still ensures majority support. ETC's approach of targeting >66% hashrate on fork-ready software is a reasonable middle ground.

6. **Constitutional constraints** — Cardano's constitution provides guardrails on what governance can do. ETC's equivalent is the Code is Law principle and community norms, enforced socially rather than programmatically.

## Sources

- [Cardano's Chang Hard Fork Goes Live — CoinDesk](https://www.coindesk.com/tech/2024/09/01/cardanos-chang-hard-fork-goes-live-introducing-on-chain-governance/)
- [Plomin Hard Fork — Bitcoin Ethereum News](https://bitcoinethereumnews.com/finance/plomin-hard-fork-will-cardanos-new-governance-survive/)
- [Cardano Shifts to Decentralized Governance — Bitcoin Ethereum News](https://bitcoinethereumnews.com/blockchain/cardano-shifts-to-decentralized-governance-a-milestone-in-blockchain-evolution/)
- [Report on Blockchain Governance Dynamics — Project Liberty](https://www.projectliberty.io/wp-content/uploads/2024/07/Submitted-to-PL-Report-on-Blockchain-Governance-Dynamics.pdf)
