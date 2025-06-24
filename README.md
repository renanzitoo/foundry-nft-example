# Foundry NFT Example

This project demonstrates a simple ERC721 (NFT) smart contract using [Foundry](https://book.getfoundry.sh/) and OpenZeppelin.

## Features

- Mint NFTs with custom token URIs
- View token URIs
- Includes example tests

## Prerequisites

- [Foundry](https://book.getfoundry.sh/getting-started/installation) installed (`forge`, `cast`)
- Node.js and npm (for some scripts, optional)
- An Ethereum RPC provider (e.g., [Infura](https://infura.io/), [Alchemy](https://alchemy.com/))
- (Optional) Etherscan API key for contract verification

## Setup

1. **Clone the repository:**
   ```sh
   git clone https://github.com/renanzitoo/foundry-nft-example.git
   cd foundry-nft-example
   ```

2. **Install dependencies:**
   ```sh
   forge install
   ```

3. **Configure environment variables:**

   Create a `.env` file in the project root:
   ```
   SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_INFURA_KEY
   PRIVATE_KEY=your_private_key
   ETHERSCAN_API_KEY=your_etherscan_api_key
   ```

   - `SEPOLIA_RPC_URL`: Your Sepolia RPC endpoint (Infura, Alchemy, etc.)
   - `PRIVATE_KEY`: Private key of the deployer account (never share this!)
   - `ETHERSCAN_API_KEY`: (Optional) For contract verification

## Usage

### Compile

```sh
forge build
```

### Test

```sh
forge test
```

### Deploy

To deploy to Sepolia (or another network), use:

```sh
make deploy ARGS="--network sepolia"
```

Or directly with forge:

```sh
forge script script/DeployBasicNft.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast
```

### Verify

If you want to verify your contract on Etherscan:

```sh
forge verify-contract --chain-id 11155111 --num-of-optimizations 2000000 --etherscan-api-key $ETHERSCAN_API_KEY DEPLOYED_CONTRACT_ADDRESS src/BasicNft.sol:BasicNft
```

## Contracts

- `src/BasicNft.sol`: The main ERC721 NFT contract

## Troubleshooting

- **Missing API keys or URLs:** Ensure your `.env` file is set up and loaded.
- **ERC721InvalidReceiver:** This error occurs if you try to mint to a contract that does not implement the ERC721 receiver interface in tests.

## License

MIT
