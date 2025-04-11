# 🧠 neurobtc Whitepaper

**A GPU-Driven Bitcoin Fork with Dual-Layer Proof of Work**

---

## 📄 1. Abstract

**neurobtc** forks Bitcoin to replace ASICs with GPUs, merging Layer 1 (L1) settlement and Layer 2 (L2) transaction clearing into a single Proof of Work (PoW) process.

- Miners secure L1 and validate L2 batches
- Enables 10,000 TPS
- Decentralization and energy efficiency

---

## 🌍 2. Introduction and Vision

Bitcoin revolutionized finance, but ASIC centralization and limited throughput restrict scale and access.

**neurobtc** envisions:
- Anyone with a GPU can participate (gamers, developers)
- Validating transactions is integrated with mining
- Microtransactions, remittances, and DeFi become viable

> **Mission**: Democratize mining, scale blockchain, align energy with real value.

---

## 🚧 3. Problem Statement

**Bitcoin Limitations:**

- **Mining Centralization**: >60% hashrate in top pools (2025)
- **Energy Waste**: ~150 TWh/year solving arbitrary puzzles
- **Scalability**: Only 7 TPS on Layer 1

> We need useful energy use, security, and decentralization.

---

## 🛠️ 4. Proposed Solution

- **GPU-Based Mining**: More accessible than ASICs
- **Dual-Layer Architecture**:
  - **L1**: High-value settlement
  - **L2**: High-throughput clearing
- **Useful PoW**: Mining validates both layers
- **Parallel Processing**: GPUs handle L1 and L2 together

---

## 🧪 5. Technical Design

### 5.1 Layer 1: Settlement

- ⏱️ **Block Time**: 10 minutes  
- 📦 **Block Size**: 2 MB (adjustable)  
- 🧩 **PoW**: GPU-friendly  
- 💰 **Purpose**: Settlement and anchoring L2

<details>
<summary>📊 L1 Merkle Tree</summary>

```
                L1 Merkle Root
                     /\
                    /  \
                   H1  H2
                  / \  / \
                 T1 T2 T3 T4
```

Explanation: L1 transactions (T1–T4) form Merkle root for block header inclusion.
</details>

<details>
<summary>🔁 L1/L2 Workflow</summary>

```
+-------------------+       +-------------------+
| L2 Nodes          |       | GPU Miners        |
| - Aggregate txs   | ----> | - Validate L2 batch|
| - Form batch      |       | - Compute L2 root |
+-------------------+       | - Mine L1 block   |
                            +-------------------+
                                   |
                                   v
+-------------------+       +-------------------+
| L1 Blockchain     | <---- | L1 Block          |
| - Stores L1 txs   |       | - L1 Merkle root  |
| - Anchors L2 roots|       | - L2 batch root   |
+-------------------+       +-------------------+
```

</details>

---

### 5.2 Layer 2: Clearing Layer

- 🧱 **Structure**: Sidechain-like batches
- 🧮 **Batch Size**: 1,000–10,000 txs (~1–10 MB)
- ⏱️ **Block Time**: 10 seconds, commits every 10 minutes
- 🔐 **Peg**: Two-way with L1
- 🔗 **Reference**: L2 batches include L1 state hash for validation

<details>
<summary>📊 L2 Merkle Tree</summary>

```
                L2 Batch Merkle Root
                     /\
                    /  \
                  H1'  H2'
                 / \   / \
               T1' T2' T3' T4'
```

</details>

---

### 5.3 GPU-Optimized Proof of Work (ProgPoW)

- ⚙️ **Design**: Optimized for GPU cores (e.g., CUDA)
- ⚡ **Performance**: ~1 GH/s on RTX 3060
- 🔀 **Parallelization**: L1 mining and L2 validation

<details>
<summary>💻 GPU Core Allocation</summary>

```
+--------------------------+
| GPU Cores                |
| +----------------------+ |
| | 20% L2 Validation   | |
| | - Signatures        | |
| | - Balances          | |
| +----------------------+ |
| +----------------------+ |
| | 80% L1 Mining       | |
| | - ProgPoW Puzzle    | |
| +----------------------+ |
+--------------------------+
```

</details>

---

### 5.4 Dual-Layer Validation

```
hash = ProgPoW(L1_header || L1_merkle_root || L2_batch_root || nonce)
if hash < difficulty_target: block is valid
```

- L1: Settlement secured by PoW
- L2: Signature, balance, and state validation
- ⚖️ Optimal GPU split: ~20% L2, ~80% L1 (adjustable)

---

### 5.5 Governance

- 🗳️ Miner signaling and community input
- 🔧 Adjustable parameters every 3 months

---

### 5.6 Architecture Overview

<details>
<summary>📡 Network Flow</summary>

```
+----------------+       +----------------+       +----------------+
| Users          | <---> | L2 Nodes       | <---> | GPU Miners     |
| - Send L1 txs  |       | - Batch txs    |       | - Mine L1      |
| - Send L2 txs  |       | - Broadcast    |       | - Validate L2  |
| - Use wallets  |       |                |       | - Anchor to L1 |
+----------------+       +----------------+       +----------------+
        |                       |                       |
        v                       v                       v
+----------------+       +----------------+       +----------------+
| L1 Blockchain  | <---- | L2 State       | <---- | L1 Blocks      |
| - Settlements  |       | - Clearing     |       | - L1/L2 Roots  |
| - L2 Anchors   |       | - Temp. state  |       |                |
+----------------+       +----------------+       +----------------+
```

</details>

---

## ⚖️ 6. Comparison to Existing Blockchains

| Feature            | neurobtc       | Bitcoin     | Ethereum   | Ravencoin  |
|--------------------|----------------|-------------|------------|------------|
| Mining Hardware     | GPUs           | ASICs       | PoS        | GPUs       |
| PoW Utility         | L1 + L2        | L1 Only     | None       | L1 Only    |
| Scalability (TPS)   | 10,000 (L2)    | 7           | ~15        | ~10        |
| Decentralization    | High (GPU)     | Moderate    | High       | High       |

> 🧠 neurobtc leads in scalability, decentralization, and useful energy.

---

## 🌐 7. Use Cases

- 💸 **Microtransactions** (e.g. tipping)
- 🌍 **Remittances** (low-cost transfers)
- ⚙️ **DeFi and Smart Contracts**
- 🤖 **IoT Payments** (machine-to-machine)

---

## 💰 8. Economic Model

- 🪙 **Total Supply**: 21 million
- 🛠️ **Block Rewards**:
  - Subsidy: 6.25 coins (halving every 4 years)
  - L1 fees
  - L2 batch fees (0.1% — 50% miners, 50% burned)
- 🧾 **L2 Tx Fee**: ~$0.01
- ❌ No Pre-Mine

---

## 🛡️ 9. Security and Sustainability

- **51% Attacks**: GPU access disperses hashrate
- **Double-Spend**: L2 commits to L1
- **ASIC Resistance**: ProgPoW + governance
- **Energy Efficiency**: Useful energy clearing $10k–$100k in value/block
- **Mitigations**:
  - Rewards for early adoption
  - Stake-based anti-botnet
  - L3 or batching for congestion

---

## 🚀 10. Roadmap

- **Q2 2025**: Testnet Launch  
- **Q3 2025**: GPU Miner + L2 Client  
- **Q4 2025**: Mainnet  
- **2026**: L2 Ecosystem  
- **2027**: Block Size Review  

---

> Join us as we reimagine mining, scale decentralized finance, and put GPUs to work for real-world value.

---
