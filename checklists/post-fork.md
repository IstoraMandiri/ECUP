# Checklist: Post-Fork

Tasks for monitoring network health after activation, handling incidents, and closing out the fork process.

## Immediate Monitoring (First 24 Hours)

- Blocks being produced at expected rate (~13 second block time)
- No chain split detected (single canonical chain)
- New consensus rules being enforced correctly
- Transaction processing working normally
- No abnormal orphan/uncle rate
- Difficulty adjustment functioning correctly
- Hashrate stable (no significant drop-off indicating miner non-upgrade)
- Block explorer(s) showing correct data

## Network Health (First 2 Weeks)

- Continued block production stability
- Node count stable or increasing
- No consensus failures or forks detected
- No reports of stuck transactions or failed contract interactions
- Mining pool distribution remains healthy (no >51% concentration)
- Gas prices and usage patterns normal

## Stakeholder Confirmation

- Exchanges have resumed deposits and withdrawals
- Major DApps confirmed operational
- Infrastructure providers (RPC, explorers, indexers) confirmed operational
- Wallet providers confirmed compatible
- No user-reported issues with funds or transactions

## Incident Response

If issues are detected:

- Issue severity classified (Critical / High / Medium / Low)
- Incident communicated to stakeholders via appropriate channels
- Root cause identified
- Fix implemented and tested
- Patched client release published (if needed)
- Post-incident report drafted

### Severity Definitions

| Severity | Description | Response Time |
|----------|-------------|---------------|
| Critical | Chain halt, consensus failure, funds at risk | Immediate (hours) |
| High | Significant performance degradation, minor chain split | Same day |
| Medium | Non-critical bugs, cosmetic issues, edge-case failures | Days |
| Low | Documentation issues, minor UX problems | Weeks |

## Closing Out

- Post-fork monitoring period complete (minimum 2 weeks, no critical issues)
- Retrospective document written covering:
  - What went well
  - What could be improved
  - Timeline adherence (actual vs. planned)
  - Stakeholder coordination effectiveness
  - Any incidents and how they were handled
- Retrospective shared with the community
- ECIP status updated to **Final**
- Any lessons learned incorporated back into this checklist repository
- Fork coordination tracking issue/document archived
