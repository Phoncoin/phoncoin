# Bootstrap specification

The Phonchain bootstrap mechanism provides an initial list of public endpoints.

## Canonical rule

A client MUST accept an endpoint only if `/network_info` returns:

genesis_hash = c098fa5e985edd56634af262975b771f0dadc607494d6875cb725f1006611658

Endpoints failing this check MUST be rejected.

## Live bootstrap URL

https://bootstrap.phonchain.org/nodes.json

## Repository copy

bootstrap/nodes.json

## Notes

- The bootstrap file does not define authority.
- Endpoints may change without requiring a wallet update.
- Canonical authority is defined by the genesis hash and consensus rules.
