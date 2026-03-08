# Proof-of-Phone (PoP) Consensus

PHONCHAIN introduces a mobile-native participation model called **Proof-of-Phone (PoP)**.

The goal is to allow real smartphones to participate in block production while reducing abuse from emulators, bots and large-scale Sybil attacks.

This document explains the general design of the PoP system.

---

# Architecture Overview

PHONCHAIN is composed of two main components.

## 1. Node (phonchain-node)

The node implements the blockchain logic and consensus rules.

Responsibilities include:

- validating heartbeats from devices
- verifying device signals and anti-emulator checks
- collecting pending transactions
- producing blocks
- distributing mining rewards
- enforcing replay protection
- exposing API endpoints used by wallets

The mining logic is implemented in the **node software**, not in the mobile wallet.

## 2. Wallet (phoncoin-wallet)

The Android wallet acts as a client.

Responsibilities include:

- generating wallet keys locally
- storing keys securely
- signing transactions on-device
- submitting mining heartbeats
- displaying balances and history
- communicating with the node API

The wallet does not contain the consensus engine.

---

# Mining Participation

Mining participation is based on **periodic heartbeats** submitted by active devices.

Each heartbeat includes:

- wallet public key
- timestamp
- device fingerprint
- nonce
- signature
- optional device signals

The wallet signs the heartbeat locally before sending it to the node.

---

# Heartbeat Validation

The node validates each heartbeat using multiple checks.

## Timestamp validation

The heartbeat must be recent enough to avoid replaying old heartbeats.

## Signature validation

The heartbeat must be signed by the wallet public key.

## Rate limiting

The node enforces participation limits per device and per public key.

## Device fingerprint binding

Each device fingerprint is associated with a wallet identity.

Rebinding can be restricted or delayed to reduce abuse.

## Emulator detection

The node can reject heartbeats originating from emulator-like environments.

---

# Anti-Sybil Mechanisms

Proof-of-Phone uses a layered defense model.

Mechanisms include:

- device fingerprint association
- server-side rate limits
- emulator detection
- device integrity signals
- optional cooldown for wallet re-binding

These mechanisms aim to make large-scale fake participation significantly harder.

---

# Block Production

Blocks are produced at a target interval of **5 minutes**.

The node monitors:

- time since last block
- number of accepted heartbeats
- transaction mempool state

When conditions are met, a new block is assembled and appended to the chain.

---

# Reward Distribution

The initial block reward is:

25 PHC per block.

With a block every 5 minutes this results in approximately:

7,200 PHC per day.

Rewards are distributed across eligible miners participating in the block.

---

# Monetary Policy

PHONCHAIN follows a **Bitcoin-style emission schedule**.

Parameters:

- Maximum supply: 21,000,000 PHC
- Initial reward: 25 PHC
- Block interval: 5 minutes
- Halving interval: 420,000 blocks

This results in a halving approximately every **4 years**, similar to Bitcoin.

---

# Transaction Model

Transactions include:

- sender public key
- recipient public key
- amount
- fee
- nonce
- timestamp
- chain_id
- signature

---

# Replay Protection

PHONCHAIN transactions include multiple replay protection mechanisms.

These include:

- chain_id validation
- sender nonce validation
- duplicate pending nonce rejection
- confirmed transaction checks

Together these mechanisms prevent replay attacks.

---

# Open Source Transparency

PHONCHAIN follows an open-source model.

The following components are publicly available:

- node implementation
- wallet implementation
- explorer
- release builds

This allows developers and users to inspect and audit the system.

---

# Summary

Proof-of-Phone is a mobile-first participation model where:

- smartphones periodically submit signed heartbeats
- nodes validate device participation
- blocks are produced every 5 minutes
- rewards follow a Bitcoin-style emission curve

The consensus logic is implemented in the node software while wallets act as secure clients.
