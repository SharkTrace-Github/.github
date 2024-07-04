# Shark Trace

Welcome to the Cryptocurrency Transaction Monitoring System repository. This system is designed to facilitate the monitoring and analysis of cryptocurrency transactions using data gathered from multiple sources. Below, you will find a comprehensive overview of the system architecture, database design, data flow, real-time alert generation, wallet attribution data collection, and the real-time KYT system.

---

## Table of Contents

- [Shark Trace](#shark-trace)
  - [Table of Contents](#table-of-contents)
  - [System Overview](#system-overview)
  - [](#)
  - [Architecture Components](#architecture-components)
    - [Users](#users)
    - [Router](#router)
    - [Firewall](#firewall)
    - [Switch](#switch)
    - [Management Nodes](#management-nodes)
    - [Intelligence Database Node](#intelligence-database-node)
    - [Crawler Database \& Server](#crawler-database--server)
    - [Cryptocurrency Nodes (BTC, Ethereum, XRP, TRON)](#cryptocurrency-nodes-btc-ethereum-xrp-tron)
    - [NAS (Network Attached Storage)](#nas-network-attached-storage)
  - [Database Design](#database-design)
    - [Overview](#overview)
    - [Collections](#collections)
      - [Wallet Summary](#wallet-summary)
      - [Transaction Data](#transaction-data)
  - [Dataflow of Ledger Indexing](#dataflow-of-ledger-indexing)
  - [Real-Time Alert Generation](#real-time-alert-generation)
  - [Wallet Attribution Data Collection and Processing](#wallet-attribution-data-collection-and-processing)
  - [Real-Time KYT System](#real-time-kyt-system)
  - [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
    - [Usage](#usage)
  - [Contributing](#contributing)
  - [License](#license)

---

## System Overview

This system is designed to monitor and analyze cryptocurrency transactions by gathering data from various sources, including the web, dark net, and blockchain networks such as Bitcoin, Ethereum, XRP, and TRON. It provides real-time data and updates, ensuring comprehensive coverage and timely insights.
![System Architecture](https://github.com/SharkTrace-Github/.github/blob/main/profile/images/system-architecture.png)
---

## Architecture Components

### Users
- **Description:** End-users who interact with the system by sending queries.

### Router
- **Description:** Entry point for user traffic, managing network traffic and directing it to the firewall.

### Firewall
- **Description:** Ensures network security by monitoring and controlling traffic based on security rules.

### Switch
- **Description:** Facilitates network communication by directing data packets between devices on the same network.

### Management Nodes
- **Description:** Handle user queries, direct them to intelligence database nodes, provide status updates, and ensure smooth operation.

### Intelligence Database Node
- **Description:** Central repository for intelligence data gathered from various sources, including OSINT and the dark net. It processes user queries and retrieves relevant information.

### Crawler Database & Server
- **Description:** Gathers data from the web and dark net, feeding intelligence data into the intelligence database node.

### Cryptocurrency Nodes (BTC, Ethereum, XRP, TRON)
- **Description:** Monitor transactions on their respective blockchain networks and provide real-time data and updates.

### NAS (Network Attached Storage)
- **Description:** Used to store large volumes of data, ensuring data is easily accessible by the intelligence and management nodes.

---

## Database Design

### Overview
The database design facilitates fetching and transforming data from a Bitcoin full node into two collections: Wallet Summary and Transaction Data. Data is managed efficiently through sharding techniques and stored in MongoDB or a distributed storage system.

### Collections

#### Wallet Summary
- **Data Stored:**
  - Wallet Address
  - Total Incoming Transactions (txs)
  - Total Outgoing Transactions (txs)
  - Value Sent
  - Value Received
  - Running Balance
- **Sharding Technique:** Partitioned at 3-month intervals.
- **Approximate Collection Size:** 30-40 million documents.

#### Transaction Data
- **Data Stored:**
  - Transaction Hash
  - Wallet Address
  - Direction
  - Value
  - Timestamp
  - Balance
- **Sharding Technique:** Partitioned at 15-day intervals.
- **Approximate Collection Size:** 20-30 million documents.

---

## Dataflow of Ledger Indexing

The dataflow involves a three-phase process for collecting, processing, and inserting Bitcoin transaction data from a Bitcoin full node into a MongoDB database:

1. **Collect**
   - **Components:** Bitcoin Full Node, RPC Call, Fetch Block, Extract Transactions, Decode the Raw Data.

2. **Process**
   - **Components:** LevelDB, Extract Output UTXO, Store Output UTXO, Fetch Inputs, Get the Transaction Data.

3. **Insert**
   - **Components:** Transform Data in JSON, Create MongoDB Collection, Wallet Summary (3 Months Interval), Transaction Data (15 Days Interval), MongoDB.

---

## Real-Time Alert Generation

The real-time alert system monitors live transactions, generates alerts based on a predefined watchlist, and categorizes these alerts for specific customers:

1. **Set Watchlist**
   - **Input Data:** Wallet Address, Customer ID, Ruleset.
   - **Generate Wallet Automation:** JSON object containing watchlist data.

2. **From Node to General Alerts**
   - **Components:** Bitcoin Node, Fetch Latest Block, Extract Transactions, Wallet Filter DB, Format Transaction, Alerts DB.

3. **From General Alerts to Rule-Based Alerts for Customers**
   - **Components:** List Input and Output Wallet Addresses, Rule Set for All Customers, Categories & Blacklist Database, Segregate and Save the Alert, Send the Alert to the Customer Table.

---

## Wallet Attribution Data Collection and Processing

The system collects and processes wallet attribution data from the web and dark web:

1. **Data Collection from Web and Dark Web**
   - **Target URL List:** Examples include OFAC, WalletExplorer, OXT.me.
   - **Crawl URL and Download Wallet Details:** Generates Raw/JSON/CSV files.

2. **Data Processing and Loading into MongoDB**
   - **Load the CSV/JSON/RAW Format**
   - **Convert Data to JSON**
   - **Shard and Load into MongoDB**

---

## Real-Time KYT System

The real-time Know Your Transaction (KYT) system assesses and generates risk scores for transactions:

1. **Input Stage**
   - **Transaction Data Input:** TransactionHash, SenderAddress, ReceiverAddress, TransactionDetails, Metadata.

2. **Processing Stage**
   - **Components:** Predefined Rule Set, Process Raw Transaction, Initiate Risk Score Generator.

3. **Validation Stage**
   - **Components:** Categories & Blacklist Database, Ledger History.

4. **Output Stage**
   - **Generate Risk Score, Category Details, and Prepare JSON**

---

## Getting Started

To get started with the system, clone this repository and follow the setup instructions provided in the [Installation Guide](INSTALLATION.md).

### Prerequisites
- MongoDB
- Node.js
- A Bitcoin Full Node
- Network Attached Storage (NAS) 

### Installation
1. Clone the repository.
2. Install the required dependencies.
3. Configure the system according to your environment.

### Usage
- Run the data collection services.
- Set up watchlists and monitoring criteria.
- Access real-time alerts and reports.

---

## Contributing

We welcome contributions from the community. Please read our [Contributing Guidelines](CONTRIBUTING.md) for more details on how to contribute.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Note:** For further information, refer to the documentation and example configurations provided in the repository.

---

*This README was generated to provide an in-depth understanding of the Cryptocurrency Transaction Monitoring System. For any queries or additional support, please contact us.*

---

[Back to Top](#shark-trace)