# liquidity-xpress (Daml)

Uses **POCA** (from `poca-infra`) as infrastructure to orchestrate claim USDCx and deposit-into-pool flows on Canton.

## Modules

| Module        | Purpose |
|---------------|---------|
| **USDCx**     | USDCxHolding and DepositAttestation; implements POCA `IHolding` and `IClaimableAttestation`. |
| **Pool**      | PoolConfig and PoolShare; implements POCA `IDepositPool` and `IShare`. |
| **Integration** | User-facing contract that calls Processor `ExecuteOnBehalfOf` for claim/deposit in one transaction. |

## Dependency

This package depends on the **poca-infra** DAR (`../poca-infra/.daml/dist/poca-infra-0.1.0.dar`). Build poca-infra first, then:

```bash
cd liquidity-xpress && dpm build
```

## Tests

Tests live in **tests/liquidity-xpress-tests**. From repo root:

```bash
dpm build --all
cd tests/liquidity-xpress-tests && dpm test
```

See the root [README](../README.md) for full workflow and architecture.
