# EtherealTrades: Decentralized NFT Marketplace

A secure and gas-optimized platform for trading Non-Fungible Tokens (NFTs) with atomic swaps and verifiable provenance through on-chain metadata indexing.

## Detailed Description

EtherealTrades is a fully decentralized NFT marketplace built on the Ethereum blockchain, designed to provide a secure, efficient, and transparent platform for creators and collectors to buy, sell, and trade NFTs. Our platform leverages smart contracts to facilitate atomic swaps, ensuring that the transfer of ownership and payment occur simultaneously, eliminating the risk of one party failing to fulfill their obligation. Furthermore, EtherealTrades prioritizes gas optimization, implementing efficient algorithms and data structures within our smart contracts to minimize transaction costs for users, making NFT trading more accessible and affordable.

A key feature of EtherealTrades is its focus on verifiable provenance. Every NFT listed on our marketplace undergoes a rigorous on-chain metadata indexing process. This involves storing comprehensive information about the NFT, including its creator, creation date, historical ownership, and any relevant attributes, directly on the blockchain. This ensures that the provenance of each NFT is immutable and verifiable by anyone, providing users with confidence in the authenticity and origin of the assets they are trading. We utilize a custom indexing solution built on top of Ethereum's event logs, making it efficient to query and retrieve historical metadata.

Beyond basic buying and selling, EtherealTrades aims to foster a vibrant community around NFTs. Future iterations will include features such as auction support, royalty enforcement for creators, and integrated social features to enable users to connect and collaborate. Our commitment to decentralization extends to the governance of the platform. As EtherealTrades evolves, we plan to introduce a decentralized autonomous organization (DAO) to allow the community to participate in decision-making regarding platform upgrades, feature development, and the overall direction of the marketplace.

## Key Features

*   **Atomic Swaps:** Smart contracts ensure secure and simultaneous transfer of ownership and payment, preventing fraudulent transactions. The `executeTrade(nftContractAddress, tokenId, price, buyer, seller)` function handles this, verifying that the NFT is owned by the seller and that the buyer has sufficient funds before executing the transfer using `safeTransferFrom` from the ERC721 standard.
*   **Gas-Optimized Contracts:** Our smart contracts are designed with gas efficiency in mind, utilizing techniques like assembly optimization and minimal storage usage to reduce transaction costs. Gas profiling was performed using Hardhat's gas reporter to identify and optimize expensive operations.
*   **On-Chain Metadata Indexing:** Comprehensive NFT metadata, including creator, history, and attributes, is stored directly on the blockchain for verifiable provenance. A custom event system triggers indexing upon NFT creation and transfer, using a mapping of `(nftContractAddress, tokenId) => MetadataStruct` for quick lookups.
*   **Royalty Enforcement:** Creators receive a percentage of each subsequent sale of their NFT, fostering a sustainable ecosystem for artists and developers. The royalty percentage is set during NFT creation and enforced by the smart contract during each sale via a `royaltyTransfer(creatorAddress, royaltyAmount)` function.
*   **Decentralized Governance (Future):** A DAO will be implemented to allow the community to participate in platform governance and decision-making. Voting will be based on staked $ETR tokens (future utility token), allowing holders to propose and vote on changes to the platform.
*   **ERC-721 and ERC-1155 Support:** EtherealTrades supports both ERC-721 and ERC-1155 standards, enabling trading of a wide variety of NFTs. The contract utilizes interfaces to interact with both standards, ensuring compatibility and flexibility.

## Technology Stack

*   **Solidity:** The core smart contracts that power the marketplace are written in Solidity.
*   **Ethereum:** The platform is deployed on the Ethereum blockchain, leveraging its security and decentralization.
*   **Hardhat:** A development environment for compiling, testing, and deploying smart contracts. We use Hardhat for local development, testing, and deployment to testnets and mainnet.
*   **OpenZeppelin:** A library of secure and audited smart contract components used for building robust and reliable systems. We leverage OpenZeppelin's ERC721 and ERC1155 implementations, as well as their access control and security modules.
*   **Python:** Used for scripting, data analysis, and off-chain components like indexing services and API integrations.
*   **Web3.py:** Python library for interacting with the Ethereum blockchain. Used to build scripts for deploying contracts and interacting with them from off-chain services.

## Installation

1.  **Clone the repository:**
    git clone https://github.com/ezozu/EtherealTrades.git
    cd EtherealTrades

2.  **Install dependencies:**
    pip install -r requirements.txt
    npm install

3.  **Install Hardhat:**
    npm install --save-dev hardhat

4.  **Compile smart contracts:**
    npx hardhat compile

## Configuration

1.  **Environment Variables:** Create a `.env` file in the root directory with the following variables:

    *   `ETHERSCAN_API_KEY`: Your Etherscan API key for contract verification.
    *   `INFURA_PROJECT_ID`: Your Infura project ID for connecting to the Ethereum network.
    *   `PRIVATE_KEY`: Your Ethereum private key for deploying contracts.  **Note:** Use a testnet private key for development.

2.  **Hardhat Configuration:** The `hardhat.config.js` file configures the Hardhat environment, including network settings, compiler versions, and API keys. Review and modify this file to suit your specific needs.

## Usage

1.  **Deploying Contracts:**

    npx hardhat deploy --network <network-name>

    Replace `<network-name>` with the desired network (e.g., `localhost`, `rinkeby`, `mainnet`). The deployment script will output the contract addresses.

2.  **Interacting with Contracts:**

    Use Web3.py to interact with the deployed contracts. Here's an example:

    import web3
    from web3 import Web3

    w3 = Web3(Web3.HTTPProvider('https://mainnet.infura.io/v3/<INFURA_PROJECT_ID>'))
    contract_address = '0x...'
    contract_abi = [...] # Load the contract ABI from the compiled JSON file
    contract = w3.eth.contract(address=contract_address, abi=contract_abi)

    # Example: Get the owner of an NFT
    token_id = 1
    owner = contract.functions.ownerOf(token_id).call()
    print(f"Owner of token {token_id}: {owner}")

3. **Indexing Service (Python):** The repository includes a Python script for indexing NFT metadata. This script connects to the Ethereum blockchain, listens for NFT creation and transfer events, and stores the relevant data in a database. The indexing service requires a database connection string and the contract address of the EtherealTrades marketplace.

## Contributing

We welcome contributions to EtherealTrades! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure your code adheres to the project's coding standards.
6.  Include unit tests for any new functionality.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/ezozu/EtherealTrades/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the OpenZeppelin team for their invaluable smart contract libraries and the Ethereum community for their ongoing support and innovation.