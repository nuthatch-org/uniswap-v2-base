# uniswap-v2-base

A [nuthatch](https://github.com/nightswatchhq/nuthatch) nest: **Uniswap V2 on Base**.

As `uniswap-v2`, re-pointed at Base. The busiest of the three.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `base`. **1 contract**, **5 tables**.

| alias | address |
|---|---|
| `factory` | `0x8909dc15e40173ff4699343b6eb8132c65e18ec6` |

## Verified

Indexed blocks **50,095,517 to 50,314,928** and sealed **173,065 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Read this before trusting it

- Crossed the RFC-0009 §4 filter flip at 798 children during verification, and decoding survived it.

## Run it

```sh
nuthatch init --from https://github.com/nightswatchhq/uniswap-v2-base
cd uniswap-v2-base
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"factory__pair_created\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
factory__pair_created
pair__burn
pair__mint
pair__swap
pair__sync
```
