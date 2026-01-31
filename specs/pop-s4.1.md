# Proof-of-Phone Secure v4.1 (PoP-S4.1)

PoP-S4.1 is a mobile-native consensus mechanism designed to secure a blockchain
using real smartphones instead of specialized hardware.

## Core principles
- One physical smartphone = one miner
- Energy-efficient heartbeat-based mining
- Strong anti-Sybil assumptions
- No ASICs, no GPUs, no PoW farms

## Heartbeat concept
A heartbeat is a signed message periodically emitted by a smartphone.
It proves:
- device presence
- liveness
- cryptographic identity
- basic device integrity signals

Heartbeats are aggregated into blocks by validator nodes.

## Security assumptions
PoP-S4.1 relies on:
- device uniqueness heuristics
- cryptographic signatures (Ed25519)
- rate-limited heartbeats
- network-level validation
- economic disincentives against mass device spoofing

## Scope
This document describes the **conceptual protocol**.
Implementation details may vary between clients.

