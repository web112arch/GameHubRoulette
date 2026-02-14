# 🎮 GameHubRoulette

GameHubRoulette is a lightweight on-chain game hub smart contract that allows logging game actions, generating pseudo-random results (gas-only roulette), and distributing prizes (native token, ERC20, ERC721, ERC1155) controlled by the contract owner.

⚠️ This contract is designed for entertainment, logging, and low-risk game mechanics.  
It is NOT suitable for real-money gambling due to weak randomness.

---

## ✨ Features

### 🎯 Game Action Logging
- `recordAction()` — Logs a basic game action
- `recordActionWithRandom()` — Logs action with pseudo-random numbers

All actions are emitted as events and can be indexed off-chain.

---

### 🎲 Gas-Only Roulette
- `spinRoulette()`
- Generates a pseudo-random number between `0` and `maxInt`
- Emits event with result
- No ETH required (only gas)

⚠️ Randomness is NOT secure and should not be used for financial value games.

---

### 🏆 Prize Distribution (Owner Only)

The contract owner can distribute prizes stored in the contract:

- Native coin (ETH / Base / EVM native)
- ERC20 tokens
- ERC721 NFTs
- ERC1155 tokens

Functions:
- `sendPrize()`
- `sendERC721Prize()`
- `sendERC1155Prize()`

---

## 🧠 Architecture

- Minimal Ownable implementation (no OpenZeppelin)
- Weak pseudo-random generator using:
  - `block.prevrandao`
  - `block.timestamp`
  - `block.num
