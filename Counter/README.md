# Counter

A minimal Solidity smart-contract project built with [Foundry](https://book.getfoundry.sh/). The `Counter` contract stores one public unsigned integer and exposes functions to set or increment it.

## Project information

| Item | Details |
| --- | --- |
| Created | 21 August 2026 |
| Solidity version | `^0.8.13` |
| Framework | Foundry (Forge) |
| Main contract | `src/Counter.sol` |
| Test suite | `test/Counter.t.sol` |
| Deployment script | `script/Counter.s.sol` |
| Test library | `forge-std` in `lib/forge-std` |

## Contract API

`Counter` has one public state variable, `number`, which Solidity exposes through an automatically generated getter: `number()`.

| Function | Description |
| --- | --- |
| `setNumber(uint256 newNumber)` | Replaces the current value with `newNumber`. |
| `increment()` | Increases the current value by one. |

## Important notes

- This is an educational/example contract. It has no ownership or access control, so any account can call `setNumber` or `increment` after deployment.
- Solidity 0.8.x reverts on arithmetic overflow, so `increment()` reverts if `number` is already `type(uint256).max`.
- The deployment script deploys a fresh `Counter` using the broadcasting account configured by Foundry. Keep private keys out of source control.

## Getting started

Install [Foundry](https://book.getfoundry.sh/getting-started/installation), then run the following from this directory:

```shell
forge build
forge test
```

Run the formatter:

```shell
forge fmt
```

## Deployment

Deploy with an RPC endpoint and a private key supplied through your shell environment:

```powershell
$env:RPC_URL = "https://your-rpc-endpoint"
$env:PRIVATE_KEY = "your-private-key"
forge script script/Counter.s.sol:CounterScript --rpc-url $env:RPC_URL --private-key $env:PRIVATE_KEY --broadcast
```

Use a test network first and never commit credentials.

## Layout

```text
src/        Solidity source contracts
test/       Forge unit and fuzz tests
script/     Forge deployment scripts
lib/        External dependencies (including forge-std)
```
