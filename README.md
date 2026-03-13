# Stacks Token Streaming

A Clarity smart contract for streaming STX token payments on the Stacks blockchain. Enables continuous, block-by-block payment flows between parties.

## Overview

Token streaming allows a sender to lock up STX tokens in a stream that gradually releases funds to a recipient over a defined block range. This is useful for:

- **Payroll** — Continuous salary payments
- **Vesting** — Token vesting schedules
- **Subscriptions** — Pay-as-you-go services

## Features

- **Create Streams** — Lock STX with a defined start/stop block and payment rate
- **Top Up Streams** — Add more STX to an existing stream
- **Withdraw Funds** — Recipients withdraw accumulated funds at any time
- **Refund Remaining** — Senders reclaim unstreamed funds after stream ends
- **Block-based Calculation** — Payments calculated per-block for precise timing

## How It Works

1. **Sender** creates a stream specifying recipient, initial balance, block range, and payment-per-block
2. STX is transferred to the contract
3. **Recipient** can withdraw accrued funds at any time based on elapsed blocks
4. After the stream ends, **sender** can reclaim any remaining balance

## Tech Stack

- **Clarity** v3 — Smart contract language for Stacks
- **Clarinet** — Development and testing toolchain
- **Vitest** — TypeScript test runner

## Getting Started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) installed

### Installation

```bash
git clone https://github.com/okekefrancis112/Stacks-Token-Streaming.git
cd Stacks-Token-Streaming
npm install
```

### Test

```bash
clarinet test
```

### Console

```bash
clarinet console
```

## Contract Interface

| Function | Access | Description |
|----------|--------|-------------|
| `stream-to` | Public | Create a new payment stream |
| `increase-balance` | Public | Top up an existing stream |
| `withdraw` | Public | Recipient withdraws accrued funds |
| `refund` | Public | Sender reclaims remaining funds (after stream ends) |
| `get-stream` | Read-only | Get stream details by ID |
| `balance-of` | Read-only | Get available balance for withdrawal |

## Project Structure

```
├── contracts/
│   └── stream.clar              # Token streaming contract
├── tests/
│   └── stream.test.ts           # Contract tests
├── deployments/                 # Deployment plans
├── settings/
│   └── Devnet.toml              # Devnet configuration
├── Clarinet.toml                # Project config
└── vitest.config.js             # Test configuration
```

## License

MIT
