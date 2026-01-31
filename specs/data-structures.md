# Data Structures (PoP-S4.1)

This document describes the canonical data formats used by Phonchain.

## Heartbeat

```json
{
  "pubkey": "hex-encoded-public-key",
  "timestamp": 1760000000,
  "nonce": 12345,
  "signature": "hex-signature",
  "device_fingerprint": "sha256(...)",
  "device_info": {
    "schema": "v4",
    "manufacturer": "...",
    "model": "...",
    "brand": "...",
    "android_version": "...",
    "sdk_int": 34,
    "is_emulator": false,
    "is_rooted": false,
    "latency_ms": 42,
    "trust_score": 90
  }
}

## Block

```json
{
  "index": 6641,
  "timestamp": 1760000300,
  "prev_hash": "...",
  "hash": "...",
  "heartbeats": [ ... ],
  "reward": 25.0,
  "miners": [ "address1", "address2" ]
}
