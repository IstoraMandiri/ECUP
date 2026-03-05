# Timelines

This document defines the standard timeline and milestones for coordinating an Ethereum Classic hard fork, from initial proposal through post-fork monitoring.

## Standard Fork Timeline

A non-contentious protocol upgrade typically takes **6-12 months** from initial ECIP draft to mainnet activation. Contentious proposals may take longer or be abandoned.

```
Month 0        Month 1-2       Month 3-4       Month 5-6       Month 7-8       Month 9+
  |               |               |               |               |               |
  v               v               v               v               v               v
PROPOSAL ──> CONSENSUS ──> IMPLEMENTATION ──> TESTNET ──> ACTIVATION ──> POST-FORK
```

---

## Phase 1: Proposal (Weeks 1-4)

**Duration:** 2-4 weeks

| Milestone | Description | Owner |
|-----------|-------------|-------|
| ECIP draft submitted | Author opens PR to ECIP repository | Proposer |
| Initial review period | Community and developers review the proposal | All |
| ECIP number assigned | Editor assigns a number and moves to Draft status | ECIP Editor |
| Specification finalized | Technical specification is complete and unambiguous | Proposer + Reviewers |

**Exit criteria:** ECIP has a number, is in Draft status, and has a complete technical specification.

---

## Phase 2: Consensus Building (Weeks 4-12)

**Duration:** 4-8 weeks

| Milestone | Description | Owner |
|-----------|-------------|-------|
| Community discussion | Open discussion on GitHub, Discord, and community calls | All |
| Stakeholder feedback collected | Key stakeholder groups have reviewed and commented | Coordinator |
| Last Call announced | ECIP moved to Last Call status with a deadline for final objections | ECIP Editor |
| Last Call period closes | Minimum 2-week Last Call period elapses without blocking objections | ECIP Editor |
| ECIP accepted | Rough consensus reached; ECIP moved to Accepted status | ECIP Editor |

**Exit criteria:** ECIP is in Accepted status with no unresolved blocking objections.

---

## Phase 3: Implementation (Weeks 8-20)

**Duration:** 4-8 weeks

| Milestone | Description | Owner |
|-----------|-------------|-------|
| Client implementation started | At least one client begins implementing the ECIP | Client developers |
| Implementation PR merged | Code merged into main client repository | Client developers |
| Second client implementation | Implementation in a second client (if applicable) | Client developers |
| Unit and integration tests | Comprehensive test coverage for the new consensus rules | Client developers |
| Devnet deployment | New rules activated on a private development network | Client developers |
| Cross-client testing | Multiple clients tested against each other on devnet | Client developers |

**Exit criteria:** At least one client has a tested implementation. Cross-client compatibility verified on devnet.

---

## Phase 4: Testnet (Weeks 16-28)

**Duration:** 4-8 weeks

| Milestone | Description | Owner |
|-----------|-------------|-------|
| Testnet activation block selected | Block height chosen for testnet activation | Core developers |
| Testnet release builds published | Client releases with testnet fork configuration | Client developers |
| Testnet fork executed | Fork activates successfully on testnet | All |
| Testnet monitoring period | Minimum 2-week observation for issues | Core developers |
| Testnet fork declared successful | No critical issues found during monitoring | Core developers |

**Exit criteria:** Testnet fork executed successfully with no critical issues over a 2+ week monitoring period.

---

## Phase 5: Activation (Weeks 24-36)

**Duration:** 4-8 weeks

| Milestone | Description | Owner |
|-----------|-------------|-------|
| Mainnet activation block proposed | Specific block height proposed (typically 4-8 weeks out) | Core developers |
| Activation block confirmed | Community agrees on the block height | All stakeholders |
| Mainnet release builds published | Official client releases with mainnet fork configuration | Client developers |
| Stakeholder notification campaign | Direct outreach to exchanges, miners, node operators | Coordinator |
| Upgrade progress tracked | Monitor node upgrade percentage via crawlers | Core developers |
| **Go/No-Go decision** | Final check ~1 week before activation: sufficient nodes upgraded? | Core developers |
| **Mainnet fork activates** | New consensus rules enforced at the activation block | Network |

**Exit criteria:** Fork activates at the designated block. Network continues producing blocks normally.

### Activation Block Selection Guidelines

- Allow **minimum 4 weeks** between release build publication and activation block
- Prefer block heights that are round numbers or meaningful milestones
- Avoid activation during major holidays or weekends (estimate based on block time)
- Account for block time variance — provide a date range, not a single date

---

## Phase 6: Post-Fork (Weeks 36+)

**Duration:** 2-4 weeks active monitoring, ongoing passive monitoring

| Milestone | Description | Owner |
|-----------|-------------|-------|
| Block production confirmed | Blocks being produced normally on the new chain | Core developers |
| No chain split detected | Monitoring confirms a single canonical chain | Core developers |
| Exchange confirmations resume | Exchanges resume deposits/withdrawals | Exchanges |
| Incident response (if needed) | Address any unexpected issues | Core developers |
| Retrospective published | Document lessons learned for future forks | Coordinator |
| ECIP status updated to Final | ECIP status updated to reflect successful activation | ECIP Editor |

**Exit criteria:** Network stable for 2+ weeks. ECIP moved to Final status. Retrospective published.

---

## Emergency Fork Timeline

In cases requiring urgent security fixes, the standard timeline may be compressed:

| Phase | Standard | Emergency |
|-------|----------|-----------|
| Proposal | 2-4 weeks | 1-3 days |
| Consensus | 4-8 weeks | 1-7 days |
| Implementation | 4-8 weeks | 1-2 weeks |
| Testnet | 4-8 weeks | 1-3 days |
| Activation | 4-8 weeks | 1-2 weeks |
| **Total** | **6-12 months** | **3-6 weeks** |

Emergency forks should only be used for critical security vulnerabilities or network-threatening issues. The compressed timeline increases risk and should be accompanied by heightened monitoring and communication.

---

## Timeline Checklist Summary

Use this as a quick reference when planning a fork:

- ECIP drafted and submitted
- ECIP number assigned, Draft status
- Community discussion period completed
- Last Call announced (minimum 2 weeks)
- ECIP moved to Accepted
- Client implementation completed and tested
- Devnet deployment and cross-client testing passed
- Testnet activation block selected
- Testnet release builds published
- Testnet fork executed and monitored (2+ weeks)
- Mainnet activation block proposed and confirmed
- Mainnet release builds published
- Stakeholder notification campaign completed
- Node upgrade progress tracked
- Go/No-Go decision made
- Mainnet fork activated
- Post-fork monitoring (2+ weeks)
- Retrospective published
- ECIP status updated to Final
