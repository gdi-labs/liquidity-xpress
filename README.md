# LiquidityXpress with POCA on Canton

This repository contains:

- **poca-infra/** — POCA as cross-chain common-good infrastructure
- **liquidity-xpress/** — App that uses POCA: Integration, USDCx, Pool
- **tests/** — Script tests for both:
  - **poca-infra-tests/** — Instruction validation, registry lookup, cross-chain step, bridge execution, CCTP receive adapter.
  - **liquidity-xpress-tests/** — Full claim+deposit flow, Integration flow, ledger-state checks, attestation validation.

## Dependencies

- Daml SDK 3.4.11
- Canton Network participant node for deployment
- xReserve / USDCx (CIP-56)

## Build and test

```bash
# Build all packages
dpm build --all

# Run POCA-only tests
cd tests/poca-infra-tests && dpm test

# Run liquidity-xpress tests (full flows)
cd tests/liquidity-xpress-tests && dpm test
```

## Package layout

| Package            | Contents                                                                 |
|--------------------|--------------------------------------------------------------------------|
| **poca-infra**     | Instruction, Registry, Interfaces (IHolding, IClaimableAttestation, IDepositPool, IShare), Processor, AdapterCCTPSend, AdapterCCTPReceive |
| **liquidity-xpress** | USDCx (implements IHolding, IClaimableAttestation), Pool (implements IDepositPool, IShare), Integration; depends on poca-infra DAR |
| **tests/poca-infra-tests** | Depends on poca-infra; tests instruction validation, registry, cross-chain, bridge, receive adapter |
| **tests/liquidity-xpress-tests** | Depends on poca-infra + liquidity-xpress; tests full claim/deposit, Integration, ledger state |
