# Checklist: Activation

Tasks for selecting the activation block, publishing release builds, and coordinating the mainnet upgrade.

## Activation Block Selection

- Testnet fork has been successful for 2 months (see [post-fork monitoring](post-fork.md))
- Mainnet activation block height proposed
- Block height allows **minimum 3 months** between release build publication and activation
- Block height avoids major holidays and weekends (estimate based on ~13s block time)
- Block height announced on ECIP PR and community channels
- Community agreement on the activation block (no objections within 1 month)

## Release Builds

- Mainnet fork configuration embedded in client code (activation block height, chain ID if changed)
- Release candidate (RC) builds published for testing
- RC tested by developers and early adopters
- Final release builds published for all supported clients:
  - Core-Geth
  - Hyperledger Besu ETC (if applicable)
  - Other clients (if applicable)
- Release notes include:
  - Activation block height and estimated date
  - Summary of changes
  - Upgrade instructions
  - Link to the ECIP

## Stakeholder Coordination

### Miners and Mining Pools
- Direct notification sent to known mining pools
- Upgrade instructions provided
- Confirmation of upgrade received from major pools (targeting >66% hashrate)

### Exchanges and Custodians
- Direct notification sent to all known exchanges listing ETC
- Deposit/withdrawal pause schedule discussed
- Replay protection details communicated (if applicable)
- Confirmation of readiness received from major exchanges

### Node Operators and Infrastructure
- Public announcement posted on ethereumclassic.org
- Notification sent to known RPC providers, block explorers, and indexers
- Upgrade instructions published and linked from the announcement

### Wallet Providers
- Notification sent to known wallet providers
- Updated chain parameters communicated

### Community
- Blog post published explaining the fork (non-technical audience)
- Social media campaign (Twitter/X, Discord, Reddit)
- FAQ document published addressing common user questions

## Pre-Activation Monitoring

- Node crawler deployed to track upgrade progress (% of nodes on fork-ready version)
- Dashboard or public tracker available showing upgrade progress
- Milestone: >50% of reachable nodes upgraded
- Milestone: >75% of reachable nodes upgraded

## Go/No-Go Decision

**Timing:** ~1 week before the estimated activation date

- Sufficient node upgrade percentage (target: >75%)
- Sufficient miner/hashrate upgrade percentage (target: >66%)
- No critical bugs discovered since release
- Major exchanges confirmed ready
- **Decision: GO** — proceed with activation at the designated block

If **NO-GO**: Communicate delay immediately, issue new client builds that push the activation block forward, and restart the activation checklist.

## Activation Day

- Core developers monitoring the network in real-time
- Communication channels staffed for questions and incident response
- Block explorer confirmed showing correct behavior post-fork
- First post-fork block validated successfully
- Network producing blocks normally
