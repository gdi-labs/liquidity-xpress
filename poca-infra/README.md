# poca-infra (Daml)

POCA (Protocol Oriented Chain Abstraction) as **cross-chain common-good infrastructure**. Provides the Processor, wire format (Instruction), registry, and CCTP adapters; apps (e.g. liquidity-xpress) implement the interfaces and use this package.

## Modules

| Module              | Purpose |
|---------------------|---------|
| **Instruction**    | POCA wire format (Header, Payload, Operation), verification. |
| **Registry**       | ActionType, RegistryEntry, (target, selector) → action lookup. |
| **Interfaces**     | IHolding, IClaimableAttestation, IDepositPool, IShare for claim/deposit orchestration. |
| **Processor**      | ProcessorConfig, Execute / ExecuteOnBehalfOf / ExecuteFromBridge / ExecuteFromBridgeWithAmount; uses interfaces only. |
| **AdapterCCTPSend** | CCTPSendRequest for cross-chain steps. |
| **AdapterCCTPReceive** | CCTPReceiveAdapter forwards to Processor ExecuteFromBridgeWithAmount. |

## Build

```bash
cd poca-infra && dpm build
```

Produces `.daml/dist/poca-infra-0.1.0.dar` for use by liquidity-xpress and test packages.

## Tests

POCA-only tests are in **tests/poca-infra-tests** (instruction validation, registry, cross-chain step, bridge execution, receive adapter). From repo root:

```bash
dpm build --all
cd tests/poca-infra-tests && dpm test
```

See the root [README](../README.md) for the full layout.
