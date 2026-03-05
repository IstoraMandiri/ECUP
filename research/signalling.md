# On-Chain Consensus Signaling Mechanisms

An overview of on-chain mechanisms that have been used (or proposed) to gauge consensus for protocol upgrades across blockchain networks. This document examines their design, historical use, strengths, and failures — and considers their relevance to Ethereum Classic.

## Miner Signaling

### How It Works

Miners embed a signal in the blocks they produce — typically by setting a version bit in the block header — to indicate readiness for a proposed protocol change. When a predefined threshold of blocks within a measurement window carry the signal, the upgrade "locks in" and activates after a grace period.

### Bitcoin: BIP 9 (Version Bits)

BIP 9 formalized miner signaling for soft fork activation:

- A specific bit in the block header's `nVersion` field is assigned to each proposal
- Signaling is measured over 2,016-block retarget periods (~2 weeks)
- A **95% threshold** triggers lock-in
- After lock-in, activation follows one retarget period later
- Each proposal has a timeout — if the threshold is not met before the timeout, the proposal expires

**Historical use:** SegWit (BIP 141) relied on BIP 9 signaling. Miners withheld signals for over a year despite broad community and developer support, effectively using the 95% threshold as veto power. This exposed a fundamental design flaw: miner signaling was intended as a **readiness check**, not a governance vote, but the high threshold transformed it into one.

### Bitcoin: BIP 8 (Version Bits with Lock-in on Timeout)

BIP 8 addressed BIP 9's shortcomings by adding a `lockinontimeout` parameter:

- If `lockinontimeout=true`, the upgrade activates at the timeout height regardless of miner signaling
- Uses block heights instead of median time past for more predictable scheduling
- Adds `minimum_activation_height` to prevent premature activation

**Historical use:** Taproot (2021) used a Speedy Trial variant of BIP 8 with `lockinontimeout=false` and a short signaling window. Miners signaled quickly, and the upgrade locked in within the first signaling period.

### Strengths

- Provides a concrete, measurable readiness signal from block producers
- Prevents activation before miners have upgraded (reducing orphan risk)
- Transparent — anyone can observe signaling in real time by inspecting block headers

### Weaknesses

- Conflates readiness with approval — miners may signal (or withhold signal) for political reasons unrelated to technical readiness
- High thresholds create de facto veto power for a minority of hashrate
- Does not capture the preferences of users, exchanges, or application developers
- In proof-of-work systems, hashrate is rented and concentrated — a small number of pool operators control signaling for a large share of the network

## User-Activated Hard Fork (UAHF)

### How It Works

A UAHF activates a hard fork at a specific block height or timestamp without requiring miner signaling. Full nodes running the new software enforce the new consensus rules from the activation point forward. The chain splits: nodes running the old rules follow one chain, nodes running the new rules follow another.

### Historical Use: Bitcoin Cash (August 2017)

Bitcoin Cash originated as a UAHF in response to the SegWit activation and perceived failure to increase the block size limit through the normal BIP process:

- Bitcoin ABC client released with a hard fork activation date of August 1, 2017
- The fork increased the block size limit from 1 MB to 8 MB
- No miner signaling threshold was required — the fork activated on a flag day
- Miners who wanted to mine BCH simply ran the new client software
- The chain split was permanent, creating two separate networks and assets

The UAHF was explicitly framed as the counterpart to UASF (BIP 148) — if users could force a soft fork without miner consent, miners could force a hard fork without user consent.

### Strengths

- Provides a clear, deterministic activation path
- Cannot be blocked by miner inaction or political maneuvering
- Gives all participants a known deadline to prepare

### Weaknesses

- Guarantees a chain split if any significant portion of the network disagrees
- No built-in mechanism to measure actual support before activation
- Can be used to bypass legitimate objections rather than resolve them
- Replay protection and other split-safety measures must be implemented explicitly

## User Signaling: CarbonVote

### How It Works

CarbonVote is an Ethereum-originated system where ETH holders signal their preference by sending a zero-value transaction to a designated contract address. Each address's vote is weighted by its ETH balance at a snapshot block. It is not binding and does not trigger any on-chain action — it functions as a **poll**, not a governance mechanism.

### Historical Use: The DAO Fork (2016)

After the DAO hack in June 2016, the Ethereum community used CarbonVote to gauge sentiment on whether to hard fork to recover the stolen funds:

- Two contract addresses were deployed — one for "yes" (fork) and one for "no" (don't fork)
- Voters sent a transaction to their chosen address; their ETH balance counted as their vote weight
- The final result showed approximately **87% in favor** of the fork (by ETH weight)
- The Ethereum Foundation cited this result as one input in the decision to proceed with the hard fork

### Problems

- **Plutocratic** — vote weight is proportional to wealth, not participation. A small number of large holders dominated the result.
- **Low turnout** — only about 5.5% of total ETH supply participated. The "87% in favor" represented a small fraction of the network.
- **Sybil-resistant but whale-dominated** — while one person couldn't cheaply create many votes, one whale could outweigh thousands of small holders.
- **Not binding** — the result was advisory only. The decision to fork was ultimately made by the Ethereum Foundation and client developers. The vote provided political cover, not technical governance.
- **Snapshot gaming** — voters could borrow ETH, vote, and return it. Balance-at-snapshot is vulnerable to flash-loan-style manipulation (though flash loans did not exist yet in 2016).
- **Selection bias** — only engaged, technically capable users participated. Exchanges holding customer funds did not vote, even though they represented significant economic weight.

### Aftermath

CarbonVote was never used again for a major Ethereum governance decision. The DAO fork — and CarbonVote's role in legitimizing it — is the event that created Ethereum Classic. The ETC community views CarbonVote as a cautionary example of how on-chain polling can be used to manufacture consent for state-modifying interventions.

## Other On-Chain Signaling Approaches

### Coin Voting (General)

Several networks use token-weighted voting for governance decisions:

- **Tezos** — bakers (validators) vote on protocol amendments as part of the self-amendment process. Amendments that pass an on-chain vote are automatically injected into the protocol.
- **Cardano** — CIP-1694 introduces on-chain governance with DReps (Delegated Representatives), a Constitutional Committee, and stake pool operators all participating in ratification votes.
- **Polkadot** — uses on-chain referenda with conviction-weighted voting (longer lock-up periods = more vote weight).

These systems differ fundamentally from CarbonVote in that their votes are **binding** — they trigger protocol changes automatically.

### Futures Markets

During contentious fork debates, futures markets have emerged as informal signaling mechanisms:

- Before the Bitcoin Cash split, exchanges listed BCH and BTC futures, allowing traders to price the expected value of each chain
- Before the DAO fork, Ethereum fork futures traded on Bitfinex and other venues
- Market prices reflect aggregated economic expectations rather than political preferences

Futures markets are not governance mechanisms, but they provide useful information about how the market values competing outcomes.

## Relevance to Ethereum Classic

ETC's governance is deliberately off-chain. The ECIP process relies on rough consensus built through discussion, review, and stakeholder outreach — not on-chain voting or miner signaling thresholds.

This is a conscious design choice rooted in ETC's origin:

1. **CarbonVote failed the community.** The DAO fork CarbonVote demonstrated that on-chain polls can be low-turnout, whale-dominated, and used to justify state modifications that violate Code is Law.

2. **Miner signaling is a readiness check, not a vote.** ETC's activation model uses a fixed block height chosen after rough consensus is established. Miners are expected to upgrade, not to approve or reject changes through signaling.

3. **On-chain governance centralizes power.** Token-weighted voting systems give disproportionate influence to large holders and can be manipulated through vote buying, delegation capture, and flash loans. ETC's permissionless discussion model is messy but resistant to plutocratic capture.

4. **Flag-day activation provides clarity.** ETC hard forks activate at a specific block height embedded in client releases. This is deterministic, easy to communicate, and does not depend on any on-chain coordination mechanism.

The question of whether ETC should adopt any on-chain signaling — even in an advisory, non-binding capacity — remains open. Any such mechanism would need to avoid the pitfalls documented above while providing genuine signal rather than manufactured consent.

## Sources

- [BIP 9: Version bits with timeout and delay](https://github.com/bitcoin/bips/blob/master/bip-0009.mediawiki)
- [BIP 8: Version bits with lock-in on timeout](https://github.com/bitcoin/bips/blob/master/bip-0008.mediawiki)
- [BIP 148: Mandatory activation of SegWit deployment](https://github.com/bitcoin/bips/blob/master/bip-0148.mediawiki)
- [UAHF: A contingency plan against UASF (Bitcoin ABC)](https://blog.bitmain.com/en/uahf-contingency-plan-uasf-bip148/)
- [CarbonVote — Ethereum Wiki](https://ethereum.org/en/governance/#dao-fork)
- [The DAO Fork — Ethereum Classic](https://ethereumclassic.org/knowledge/forks/)
- [On-chain governance overview — Messari](https://messari.io/report/on-chain-governance)
