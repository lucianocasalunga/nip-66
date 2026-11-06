# NIP-66 · Relay Liveness Monitoring on LiberNet

> Relay Liveness Monitoring, as used by the **LiberNet** apps.

**Official spec:** [nostr-protocol/nips · 66.md](https://github.com/nostr-protocol/nips/blob/master/66.md)
**Status upstream:** `draft` `optional` `relay`
**Maintainer of this repo:** Luciano "Barak" Casalunga ([@lucianocasalunga](https://github.com/lucianocasalunga)) · [libernet.app](https://libernet.app)

## My role

I took part in the creation of NIP-66, and it runs across the LiberNet apps.

## Why NIP-66 matters for LiberNet

LiberNet runs its own relays and cares about which relays are alive and fast. NIP-66 is the standard way to publish that: monitors probe relays and publish signed reports any client can read.

## How it works (quick reference)

| Kind  | Purpose |
|-------|---------|
| 30166 | Relay discovery: one event per relay (`d` = relay URL) |
| 10166 | Relay monitor announcement (frequency, checks performed) |

Common tags in `30166`: `rtt-open`, `rtt-read`, `rtt-write`, `n` (clearnet/tor/i2p), `N` (supported NIPs), `R` (requirements like `auth`, `!payment`), `t` (topics), `g` (geohash).

### Example: a report about the LiberNet relay

```json
{
  "kind": 30166,
  "pubkey": "<monitor pubkey>",
  "tags": [
    ["d", "wss://relay.libernet.app/"],
    ["n", "clearnet"],
    ["N", "50"], ["N", "70"], ["N", "77"],
    ["rtt-open", "120"]
  ]
}
```

## Related LiberNet NIPs

[NIP-43](https://github.com/lucianocasalunga/nip-43) · [NIP-45](https://github.com/lucianocasalunga/nip-45) · [NIP-50](https://github.com/lucianocasalunga/nip-50) · [NIP-67](https://github.com/lucianocasalunga/nip-67) · [NIP-70](https://github.com/lucianocasalunga/nip-70) · [NIP-77](https://github.com/lucianocasalunga/nip-77) · [NIP-86](https://github.com/lucianocasalunga/nip-86) · [NIP-95 (my proposal)](https://github.com/lucianocasalunga/nip-95)

---
Nostr since 2021 · Part of the LiberNet ecosystem
