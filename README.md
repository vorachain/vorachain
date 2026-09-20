# VORA Chain

**A public EVM Layer 1 — chain ID 3318, native coin VRA.**

VORA Chain runs Hyperledger Besu with QBFT consensus: two-second blocks, immediate finality, and full
EIP-155 / EIP-1559 support. Everything on the network is open to inspect through a public RPC endpoint
and a Blockscout explorer.

---

## Network

| | |
|---|---|
| Chain ID | `3318` (`0xCF6`) |
| Native coin | VORA — symbol `VRA`, 18 decimals |
| RPC | `https://vorascan.io/rpc` |
| Explorer | https://vorascan.io (Blockscout, EIP-3091) |
| Client | Hyperledger Besu 26.8.0 |
| Consensus | QBFT (proof of authority) |
| Block time | 2 seconds |
| EVM version | London |

## Add VORA to your wallet

In MetaMask: **Settings → Networks → Add a network manually**, then enter

```
Network name:     VORA Chain
RPC URL:          https://vorascan.io/rpc
Chain ID:         3318
Currency symbol:  VRA
Block explorer:   https://vorascan.io
```

## Building on VORA

- **Compile for the London EVM.** Set `evmVersion: "london"` (or `paris`) in Hardhat, Foundry or Remix.
  Solidity 0.8.20 and later default to Shanghai, which emits `PUSH0` — that opcode is rejected here and the
  deployment fails.
- **Fees are EIP-1559,** and the network enforces a minimum gas price together with a matching priority-fee
  floor. Read the current value from `eth_gasPrice` rather than hard-coding one. A transaction sent below the
  floor is never mined; it can be pushed through again at [vorascan.io/tools/pending](https://vorascan.io/tools/pending/).
- **Uniswap V2 is deployed** and byte-identical to the Ethereum mainnet contracts, including the init code hash:

  | Contract | Address |
  |---|---|
  | WVRA (wrapped VRA) | `0xfDFf1d525038Eb287314e9A2cC8fE48AA6629Cb9` |
  | UniswapV2Factory | `0xCE194EF7eAC3022880525217e85A331D436b6539` |
  | UniswapV2Router02 | `0x80FC3e2C1D74cd15F5e78B116142cEA24208eA36` |

## Ecosystem

| | |
|---|---|
| Website | https://vorachain.com |
| Explorer | https://vorascan.io |
| Documentation | https://vorachain.gitbook.io/vorachain-docs |
| DEX | https://voradex.io |
| Validator staking | https://vorascan.io/staking/ |
| Stuck transaction tool | https://vorascan.io/tools/pending/ |

## Listing status

VORA Chain has been submitted to the public chain registries that wallets and dapps read from:

- [ethereum-lists/chains#8737](https://github.com/ethereum-lists/chains/pull/8737) — feeds chainid.network,
  wallets and tooling
- [DefiLlama/chainlist#3167](https://github.com/DefiLlama/chainlist/pull/3167) — feeds chainlist.org
