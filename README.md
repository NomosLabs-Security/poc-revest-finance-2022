# Revest Finance — ERC1155 Mint Callback Reentrancy PoC

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It is a simplified simulation, not a fork replay against mainnet.

**Date:** 2022-03-27 | **Loss:** $2M | **Chain:** Ethereum

## Quick Start
```bash
git clone https://github.com/NomosLabs-Security/poc-revest-finance-2022
cd poc-revest-finance-2022
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Vulnerability
Revest Finance's `mintAddressLock()` minted ERC1155 FNFT tokens to the caller, triggering `onERC1155Received` callback. The FNFT ID counter was incremented AFTER the mint, allowing re-entrant calls to get the same ID and create duplicate allocations.

## Key Contracts
- `src/Exploit.sol` — Vulnerable FNFT minting with ERC1155 callback reentrancy
- `test/Exploit.t.sol` — Foundry test demonstrating the exploit

## License

MIT — For educational use only.
