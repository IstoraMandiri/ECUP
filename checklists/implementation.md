# Checklist: Implementation

Tasks for implementing the accepted ECIP in client software and validating correctness through testing.

## Client Implementation

- Primary client (Core-Geth) implementation started
- Implementation follows the ECIP specification exactly — no undocumented deviations
- Code review completed by at least one other developer
- Implementation PR merged into the client repository
- Secondary client implementation started (if applicable, e.g., Hyperledger Besu ETC)
- Secondary client PR merged

## Test Development

- Unit tests cover all new consensus rules
- Edge cases and boundary conditions tested
- Tests for backwards compatibility (pre-fork blocks must still validate)
- Test vectors documented and shareable across client implementations
- Negative tests (invalid blocks/transactions that should be rejected post-fork)

## Devnet Deployment

- Private devnet launched with fork-ready client(s)
- Fork activated on devnet at a test block height
- Basic functionality verified:
  - Blocks produced normally after fork activation
  - New consensus rules enforced correctly
  - Pre-fork transactions and contracts still function
  - New opcodes/precompiles work as specified (if applicable)
- Cross-client compatibility verified on devnet (if multiple clients)
- Stress testing performed (high transaction volume, edge-case blocks)
- No consensus failures or unexpected chain splits on devnet

## Security Review

- Implementation reviewed for potential security vulnerabilities
- Gas cost changes analyzed for DoS vectors (if applicable)
- No regressions in existing security properties
- If the fork includes EVM changes, fuzzing performed against the new rules

## Documentation

- ECIP updated with links to implementation PRs
- Release notes drafted for the upcoming client release
- Upgrade guide drafted for node operators (any new configuration needed?)
- Known issues or caveats documented

## Exit Criteria

- At least one client has a fully tested implementation
- All tests passing on devnet
- No known critical bugs
- Ready to proceed to testnet deployment
