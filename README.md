# Foundry NFT

A Solidity / Foundry project featuring two ERC-721 NFT contracts built as part of the [Cyfrin Foundry Full Course](https://github.com/Cyfrin/foundry-full-course-f23).

---

## Contracts

### BasicNft (`Dogie` / `DOG`)

A straightforward ERC-721 where the caller supplies a token URI at mint time. The default interaction script mints a **Shiba Inu** image stored on IPFS.

| Function | Description |
|---|---|
| `mintNft(string tokenUri)` | Mint an NFT with a custom token URI |
| `tokenURI(uint256 tokenId)` | Returns the stored URI for a token |

### MoodNft (`Mood NFT` / `MN`)

A fully **on-chain** SVG NFT. Metadata and images are Base64-encoded and stored directly in the contract — no IPFS or external hosting required. Each token starts `HAPPY`; the owner can flip it to `SAD` and back.

| Function | Description |
|---|---|
| `mintNft()` | Mint a new Mood NFT (starts HAPPY) |
| `flipMood(uint256 tokenId)` | Toggle the mood between HAPPY 😊 and SAD 😢 |
| `tokenURI(uint256 tokenId)` | Returns on-chain Base64-encoded JSON metadata |

---

## Getting Started

### Prerequisites

- [Foundry](https://getfoundry.sh/) (`forge`, `cast`, `anvil`)
- [Git](https://git-scm.com/)

### Installation

```bash
git clone https://github.com/AztecWarlord/foundry-nft-f23
cd foundry-nft-f23
make install
```

### Environment Variables

Create a `.env` file for testnet / mainnet deployments:

```env
PRIVATE_KEY=<your-wallet-private-key>
SEPOLIA_RPC_URL=<your-sepolia-rpc-url>
ETHERSCAN_API_KEY=<your-etherscan-api-key>
```

---

## Usage

### Build

```bash
make build
# or
forge build
```

### Test

```bash
make test
# or
forge test
```

### Format

```bash
make format
```

### Local Development (Anvil)

```bash
make anvil
```

---

## Deployment

### Deploy BasicNft

```bash
# Local Anvil
make deploy

# Sepolia testnet
make deploy ARGS="--network sepolia"
```

### Deploy MoodNft

```bash
# Local Anvil
make deployMood

# Sepolia testnet
make deployMood ARGS="--network sepolia"
```

### Mint a BasicNft

```bash
make mint
```

### Mint a MoodNft (local Anvil)

```bash
make mintMood
```

---

## Project Structure

```
├── src/
│   ├── BasicNft.sol         # Simple ERC-721 with external token URI
│   └── MoodNft.sol          # On-chain SVG ERC-721 with flippable mood
├── script/
│   ├── DeployBasicNft.s.sol
│   ├── DeployMoodNft.s.sol
│   └── Interactions.s.sol   # MintBasicNft interaction script
├── test/
│   ├── unit/
│   │   ├── BasicNftTest.t.sol
│   │   └── MoodNft.t.sol
│   └── integrations/
│       ├── MoodNftIntegration.t.sol
│       └── DeployMoodNftTest.t.sol
└── images/
    ├── happy.svg
    ├── sad.svg
    └── shiba-inu.png
```

---

## Dependencies

| Library | Version |
|---|---|
| [forge-std](https://github.com/foundry-rs/forge-std) | v1.5.3 |
| [openzeppelin-contracts](https://github.com/OpenZeppelin/openzeppelin-contracts) | v4.8.3 |
| [foundry-devops](https://github.com/Cyfrin/foundry-devops) | 0.0.11 |

---

## License

MIT
