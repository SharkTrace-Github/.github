# Shark Trace

Welcome to the Cryptocurrency Transaction Monitoring System repository. This system is designed to facilitate the monitoring and analysis of cryptocurrency transactions using data gathered from multiple sources. Below, you will find a comprehensive overview of the system architecture, database design, data flow, real-time alert generation, wallet attribution data collection, and the real-time KYT system.

---

## Table of Contents

- [Shark Trace](#shark-trace)
  - [Table of Contents](#table-of-contents)
  - [System Overview](#system-overview)
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

---

## System Overview

This system is designed to monitor and analyze cryptocurrency transactions by gathering data from various sources, including the web, dark net, and blockchain networks such as Bitcoin, Ethereum, XRP, and TRON. It provides real-time data and updates, ensuring comprehensive coverage and timely insights.
<br>
<br>
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



