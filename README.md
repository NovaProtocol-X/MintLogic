# MintLogic

> Institutional asset issuance factory with protocol-level compliance on Stellar

---

## Overview

MintLogic is an **institutional asset issuance factory** built on Stellar. It automates regulatory compliance at the protocol level using **SEP-8** (Regulated Assets) and **Clawback** mechanisms. Every asset movement is verified against an off-chain approval server before execution, ensuring all transactions are audit-ready and regulatorily compliant.

MintLogic is built for institutions, asset issuers, and regulated entities that need programmable compliance baked into the asset layer itself.

---

## Features

- **SEP-8 Integration** — Regulated Asset standard for on-chain compliance gating
- **Clawback Support** — Protocol-level asset recall for regulatory enforcement
- **Approval Server** — Off-chain verification layer for every asset movement
- **Regulatory Auditability** — Full transaction trail for compliance reporting
- **Issuance Automation** — Streamlined factory pattern for creating compliant assets at scale

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/)
- [Stellar CLI](https://developers.stellar.org/docs/tools/developer-tools)
- Issuer keys for your Stellar account
- `make`

### Installation

**1. Set up the approval server:**
```bash
cd packages/approval-server && npm install
```

**2. Configure your assets:**

Edit `config.json` with your issuer keys and asset parameters:
```json
{
  "issuerSecret": "S...",
  "assetCode": "MYASSET",
  "approvalCriteria": { ... }
}
```

**3. Deploy the compliance hooks:**
```bash
make deploy-hooks
```

---

## Project Structure

```
mintlogic/
├── packages/
│   └── approval-server/    # Off-chain SEP-8 approval server
├── contracts/              # On-chain compliance hooks
├── config.json             # Issuer and asset configuration
├── Makefile                # Deploy commands
└── CONTRIBUTING.md         # Contribution guidelines
```

---

## How It Works

1. An asset is issued through MintLogic's factory using your configured issuer keys
2. Every transfer is intercepted by the **SEP-8 approval server**, which applies your compliance rules
3. Approved transactions proceed on-chain; rejected ones are blocked at the protocol level
4. Clawback flags allow issuers to recall assets if regulatory action is required
5. All events are logged for **regulatory auditability**

---

## Contributing

MintLogic contributions are focused on **regulatory standards** and compliance tooling. See [CONTRIBUTING.md](./CONTRIBUTING.md) for current open tasks and the contribution process.

---

## License

This project is licensed under the [Apache 2.0 License](./LICENSE).
