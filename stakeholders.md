# Stakeholders

This document identifies the groups that participate in, signal support for, or are affected by Ethereum Classic hard forks. Each group has different roles, concerns, and communication channels.

## Core Stakeholder Groups

### 1. Protocol Developers

**Role:** Write, review, and implement ECIPs. Maintain client software (Core-Geth, Hyperledger Besu ETC, etc.).

**Concerns:**
- Technical correctness and security of proposed changes
- Backwards compatibility and upgrade complexity
- Testing coverage and confidence in activation logic
- Maintainability of client codebases

**Signal:** Merge ECIP implementations into client repositories; publish release candidates.

**Communication:** GitHub (ECIP repo, client repos), developer calls, Discord.

### 2. Miners and Mining Pools

**Role:** Secure the network via proof of work. Must upgrade mining software to follow new consensus rules.

**Concerns:**
- Impact on mining profitability (block rewards, DAG changes, algorithm changes)
- Sufficient lead time to upgrade infrastructure
- Network stability during transition (orphan rates, difficulty adjustments)
- Hardware compatibility (e.g., DAG size affecting GPU viability)

**Signal:** Upgrade to fork-ready client versions; hashrate on the new chain post-fork.

**Communication:** Mining pool announcements, community forums, direct outreach.

**Note:** As the largest PoW smart contract platform, miner coordination is especially critical for ETC. The Thanos (ECIP-1099) fork was specifically designed to address miner hardware concerns.

### 3. Node Operators

**Role:** Run full nodes that validate transactions and propagate blocks. Includes independent operators, infrastructure providers, and RPC endpoint operators.

**Concerns:**
- Upgrade complexity and downtime requirements
- Disk space, sync time, and resource requirements of new features
- Adequate notice period before activation block

**Signal:** Upgrade nodes to fork-ready versions.

**Communication:** Blog posts, social media announcements, direct outreach to known operators.

### 4. Exchanges and Custodians

**Role:** Provide ETC trading, custody, and on/off-ramp services. Must handle deposit/withdrawal pauses, chain validation, and replay protection.

**Concerns:**
- Replay protection between old and new chains
- Sufficient confirmation depth requirements during fork transition
- Clear communication timelines for deposit/withdrawal pauses
- Risk of chain splits creating duplicate balances
- Regulatory and compliance implications of fork outcomes

**Signal:** Public announcements of fork support; resume deposits/withdrawals on the new chain.

**Communication:** Direct outreach (email, dedicated exchange relations contacts), public blog posts.

### 5. Wallet Providers

**Role:** Provide software or hardware wallets supporting ETC. Must update chain parameters, RPC endpoints, and transaction logic.

**Concerns:**
- Updated chain IDs, gas calculations, or transaction formats
- User-facing communication about required updates
- Compatibility testing with new consensus rules

**Signal:** Release updated wallet versions supporting the fork.

**Communication:** Direct outreach, developer documentation.

### 6. DApp Developers and Smart Contract Deployers

**Role:** Build applications on Ethereum Classic. Affected by changes to the EVM, gas costs, or opcode availability.

**Concerns:**
- Breaking changes to existing smart contracts
- New opcodes or precompiles that enable new functionality
- Gas cost changes affecting contract economics
- Tooling compatibility (Solidity versions, development frameworks)

**Signal:** Test and validate contracts on testnet; public statements of readiness.

**Communication:** Developer forums, documentation updates, Discord.

### 7. Infrastructure and Service Providers

**Role:** Operate block explorers, RPC providers, indexers, oracles, bridges, and other middleware.

**Concerns:**
- API compatibility and data format changes
- Indexing and database migration requirements
- Service continuity during the fork window

**Signal:** Update services; confirm compatibility publicly.

**Communication:** Direct outreach, status pages.

### 8. Community and Ecosystem Organizations

**Role:** Advocacy, education, and coordination. Includes the ETC Cooperative, community DAOs, media outlets, and educator channels.

**Concerns:**
- Clear, accurate public communication about fork purpose and timeline
- Alignment with ETC's core principles (Code is Law, immutability, PoW)
- Community sentiment and potential for contentious splits

**Signal:** Public endorsements, educational content, social media support.

**Communication:** Blog posts, social media, community calls, conferences.


### 9. End Users and Token Holders

**Role:** Hold ETC, use dApps, and transact on the network. Generally passive participants but the ultimate source of network value.

**Concerns:**
- Safety of funds during the fork
- Whether any action is required on their part
- Clear, non-technical explanations of what the fork means

**Signal:** Continue using the network post-fork; market behavior.

**Communication:** Blog posts, social media, wallet notifications, exchange announcements.

---

## Stakeholder Engagement Matrix

| Stakeholder | Must Signal Before Fork | Must Upgrade Software | Notification Lead Time | Criticality |
|-------------|:-----------------------:|:---------------------:|:----------------------:|:-----------:|
| Protocol Developers | Yes | Yes | Involved from proposal | Critical |
| Miners / Mining Pools | No (implicit via upgrade) | Yes | 4-8 weeks minimum | Critical |
| Node Operators | No (implicit via upgrade) | Yes | 4-8 weeks minimum | Critical |
| Exchanges / Custodians | Yes (recommended) | Yes | 6-8 weeks minimum | Critical |
| Wallet Providers | No | Yes | 4-6 weeks minimum | High |
| DApp Developers | No | Depends on changes | 4-6 weeks minimum | Medium |
| Infrastructure Providers | No | Yes | 4-6 weeks minimum | High |
| Community Organizations | Yes (recommended) | No | 2-4 weeks minimum | Medium |
| End Users | No | No (wallet may need update) | 2-4 weeks minimum | Low |

## Communication Channels

- **GitHub:** Primary venue for ECIP discussion and technical review
- **Discord:** Real-time community coordination (Ethereum Classic Discord)
- **Twitter/X:** Public announcements and sentiment
- **ETC Cooperative Blog:** Official ecosystem communications
- **ethereumclassic.org:** Fork announcements and upgrade guides
- **Direct Outreach:** Email and private channels for exchanges and major infrastructure
