# Paytrace
![Paytrace logo](assets/logo.png)

Programmable micropayments and verifiable receipts for AI agents on Solana.

## Overview

Paytrace lets autonomous AI agents pay each other for API calls, data, or compute using streaming USDC micropayments on Solana, with every transaction logged as a verifiable on-chain receipt. Developers get a simple SDK that wraps any HTTP endpoint with a pay-per-call paywall, similar to HTTP 402 but settled instantly on-chain.

## Problem

AI agents calling paid APIs or other agents have no native way to pay per request without subscriptions, API keys, or manual billing. This is a blocker for machine-to-machine commerce in an agentic AI world.

## Solution

A Solana-based SDK and relayer that turns any HTTP request into a pay-per-call transaction, settled instantly in USDC, with an on-chain receipt for auditability.

## Features (MVP)

- SDK middleware that adds a 'pay-per-call' header to any REST endpoint
- Instant USDC micropayment settlement via Solana Pay / SPL transfers
- On-chain receipt (NFT or compressed log) proving each paid request
- Dashboard to track agent spend and earnings across services
- Simple escrow for streaming payments during long-running agent tasks

## Tech Stack

- Rust, Anchor (on-chain program)
- Solana Pay, USDC/SPL Token (settlement)
- Compressed NFTs / state compression (receipts)
- Node.js SDK (developer-facing middleware)

## How It Works

```
Agent A (buyer)            Wrapped API (seller)           Solana
     |                           |                           |
     | 1. HTTP request --------->|                           |
     |<--- 402 payment required--|                           |
     | 2. USDC micropayment ---------------------------------->
     |                           |<--- 3. payment confirmed--|
     |<--- 4. API response ------|                           |
     |                           | 5. compressed receipt logged on-chain
```

1. An agent calls an HTTP endpoint wrapped with the Paytrace SDK.
2. The server responds with a pay-per-call request (402-style).
3. The agent's wallet settles a USDC/SPL micropayment via Solana Pay.
4. On confirmation, the API responds normally.
5. A compressed on-chain receipt (or receipt NFT) is created, proving the paid request happened. For long-running tasks, a simple Anchor-based escrow streams payments over time instead of a single lump sum.

## Roadmap

- Partner with AI agent frameworks (LangChain, AutoGPT-style) for native integration
- Add support for streaming/metered payments for compute-heavy tasks
- Build a marketplace directory of pay-per-call AI services

## Pitch

- [Pitch deck (PDF)](docs/pitch.pdf)
- [Pitch script](docs/pitch-script.md)

## Team

- Name — Role — [GitHub](#) / [Twitter](#)
- Name — Role — [GitHub](#) / [Twitter](#)
- Name — Role — [GitHub](#) / [Twitter](#)

---

🎬 Pitch video: [docs/pitch-video.mp4](docs/pitch-video.mp4)


## Prototype

Live prototype: https://yuma0204.github.io/paytrace/

The source is [docs/index.html](docs/index.html) (served with GitHub Pages from the /docs folder). All data is simulated.
