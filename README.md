# BeaconWatch: Decentralized Real-Time Crypto Price Alerts

BeaconWatch provides a decentralized, real-time cryptocurrency price alert system delivered via WebSockets, utilizing smart contract oracles and verifiable compute for tamper-proof notifications. This system ensures users receive timely and accurate price alerts without relying on centralized data providers, mitigating the risks of data manipulation and single points of failure.

BeaconWatch leverages the power of decentralized oracles to fetch cryptocurrency price data from multiple sources, aggregating them through a smart contract on a blockchain (e.g., Ethereum). This aggregated data is then verified using verifiable compute, ensuring the integrity and accuracy of the price information. A backend service, built with TypeScript and utilizing WebSockets, subscribes to these on-chain price feeds and pushes real-time alerts to users based on their pre-defined criteria. This architecture ensures that price alerts are both reliable and transparent. The system is designed to be modular and extensible, allowing for the integration of different oracle solutions, verifiable compute platforms, and blockchain networks.

The primary goal of BeaconWatch is to provide a robust and trustworthy alternative to traditional centralized price alert services. By leveraging blockchain technology and verifiable compute, BeaconWatch guarantees the integrity of price data and minimizes the risk of manipulation. This is particularly crucial in the volatile cryptocurrency market, where timely and accurate information is essential for making informed trading decisions. Furthermore, the decentralized nature of the system enhances its resilience and availability, ensuring that users receive alerts even in the event of infrastructure failures or malicious attacks targeting centralized servers.

## Key Features

*   **Decentralized Price Oracles:** Employs smart contract oracles (e.g., Chainlink, Band Protocol) to fetch price data from multiple exchanges, mitigating single points of failure. The contracts are written in Solidity and deployed on a supported blockchain. (e.g., Ethereum mainnet, Goerli testnet).
*   **Verifiable Compute Integration:** Integrates with verifiable compute platforms (e.g., Truebit, Arbitrum) to ensure the accuracy and integrity of price data before alerts are triggered. This involves submitting the price data to the verifiable compute platform along with the computation logic and receiving cryptographic proof of its correctness.
*   **Real-time WebSocket Notifications:** Delivers price alerts to users in real-time via WebSockets. The WebSocket server is built using Node.js and a WebSocket library such as `ws` or `socket.io`.
*   **Customizable Alert Thresholds:** Allows users to define custom price thresholds and conditions for triggering alerts. These thresholds are stored in a database and used by the backend service to determine when to send alerts.
*   **Support for Multiple Cryptocurrencies:** Supports a wide range of cryptocurrencies and trading pairs. The list of supported cryptocurrencies is configurable and can be easily extended.
*   **Smart Contract Interaction Library:** Provides a TypeScript library for interacting with the smart contracts, simplifying the process of fetching price data and subscribing to price updates. This library handles the complexities of interacting with the blockchain.
*   **User Authentication and Authorization:** Implements user authentication and authorization to ensure that only authorized users can access and manage their alerts.

## Technology Stack

*   **TypeScript:** Used for the backend service, smart contract interaction library, and client-side application (if any) due to its strong typing and scalability.
*   **Node.js:**  A JavaScript runtime environment for executing the backend service and WebSocket server.
*   **Solidity:** Used for writing the smart contracts that fetch and aggregate price data from oracles.
*   **WebSockets:** Used for real-time communication between the backend service and client applications.
*   **Blockchain (e.g., Ethereum):** Provides the decentralized infrastructure for storing and verifying price data.
*   **Smart Contract Oracles (e.g., Chainlink, Band Protocol):**  External data providers that feed price data into the smart contracts.
*   **Verifiable Compute (e.g., Truebit, Arbitrum):**  Used to verify the integrity of price data and computation logic.
*   **Database (e.g., PostgreSQL, MongoDB):** Used for storing user data, alert configurations, and other application data.

## Installation

1.  Clone the repository:
    `git clone https://github.com/uhsr/BeaconWatch.git`
2.  Navigate to the project directory:
    `cd BeaconWatch`
3.  Install dependencies:
    `npm install` or `yarn install`
4.  Install dependencies for contracts (navigate to `/contracts` directory):
    `npm install` or `yarn install`
5. Compile the smart contracts (navigate to `/contracts` directory):
    `npx hardhat compile`
6. Deploy the smart contracts to a testnet or mainnet (refer to the smart contract documentation for deployment instructions. Consider using `npx hardhat deploy --network <network_name>`).
7.  Copy the `.env.example` file to `.env` and update the environment variables (see Configuration section).
    `cp .env.example .env`

## Configuration

The following environment variables need to be configured in the `.env` file:

*   `NODE_ENV`:  The environment the application is running in (e.g., `development`, `production`).
*   `PORT`: The port the WebSocket server will listen on (e.g., `3000`).
*   `DATABASE_URL`: The connection string for the database.
*   `ETHEREUM_RPC_URL`: The URL of the Ethereum RPC endpoint. (e.g., Infura or Alchemy).
*   `PRIVATE_KEY`: The private key of the Ethereum account used to interact with the smart contracts.
*   `CONTRACT_ADDRESS`: The address of the deployed smart contract.
*   `VERIFIABLE_COMPUTE_API_KEY`: The API key for the verifiable compute platform (if applicable).
*   `WS_ORIGIN`: The origin of the WebSocket connection (e.g., `http://localhost:8080`).

## Usage

To start the WebSocket server:

`npm run start` or `yarn start`

The server will listen for WebSocket connections on the configured port.  Clients can connect to the server and subscribe to price alerts by sending a JSON message with the following format:

Example:


To unsubscribe:



The server will send price alerts to clients when the specified threshold is reached. The alerts will be sent in the following format:



A comprehensive API documentation with all endpoints and data structures will be provided in a separate document.

## Contributing

We welcome contributions to BeaconWatch! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure all tests pass before submitting your pull request.
6.  Adhere to the coding style and conventions used in the project.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/uhsr/BeaconWatch/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to acknowledge the following open-source projects and communities that have contributed to the development of BeaconWatch:

*   Chainlink
*   Ethereum
*   Node.js
*   TypeScript