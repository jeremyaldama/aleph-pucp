# Aleph | Collective Commerce Infrastructure

Private Avalanche L1 infrastructure for coordinated retail procurement, tokenized orders, and transparent supplier financing.

## Problem

Small neighborhood retailers operate in fragmented, low-trust supply chains:

- They buy in small volumes and cannot negotiate competitive prices.
- They usually have limited or expensive access to working capital.
- Suppliers see uncertain demand and higher distribution risk.
- Repayment agreements are often informal and hard to audit.

The result is a financing gap: good businesses cannot grow because they cannot prove collective demand or repayment performance.

## Solution

Aleph coordinates many retailers into one financeable order flow:

- Demand aggregation: multiple stores commit purchase intent into a shared procurement pool.
- Supplier financing: a distributor or supplier can fund the pooled order with better visibility.
- RWA tokenization: the aggregated order is represented on-chain as a tokenized real-world asset.
- Repayment transparency: obligations and lifecycle events are tracked in one auditable system.
- Liquidity path: cross-L1 interoperability opens a route to public-chain capital and liquidity.

## How It Works

1. Create pool
   A supplier or coordinator opens a permissioned pool for a product campaign.
2. Stores join
   Eligible retailers submit commitments (quantity, SKU, target terms).
3. Supplier funds
   The supplier finances the aggregated order once the pool meets threshold conditions.
4. Order is tokenized
   The aggregated order is structured and tokenized as an RWA representation.
5. Goods delivered
   Physical goods are delivered to participating retailers through normal logistics.
6. Stores repay
   Repayments are recorded against transparent obligations, improving credit visibility for future cycles.

## Why Avalanche

Aleph is designed around Avalanche because the architecture matches institutional B2B requirements:

- Private Avalanche L1
  Dedicated execution environment for business logic, predictable policy, and controlled participant access.
- Permissioned validators
  Validators can be limited to approved entities for regulated enterprise workflows.
- Encrypted transfers
  Sensitive commercial flows (volume, counterparties, settlement terms) can preserve confidentiality.
- Cross-L1 interoperability
  Bridge pathways allow selected assets or states to connect to public Avalanche for broader financing and liquidity.

## Architecture

- Frontend ([aleph-front](aleph-front))
  Role-based dashboards for retailers and suppliers, campaign actions, and transaction activity views.
- Backend ([aleph-back](aleph-back))
  NestJS orchestrator for auth, merchant verification, order aggregation, lifecycle handling, and contract interactions.
- Smart contract layer
  Pool management and tokenization/lifecycle contract interfaces (ABIs in [aleph-back/abis](aleph-back/abis)).
- Private Avalanche L1
  Target settlement layer for permissioned execution and enterprise-grade transaction control.

## MVP Scope (Hackathon)

What is implemented now:

- End-to-end app skeleton with role-based frontend and modular backend services.
- Coordinated pool and order-lifecycle orchestration in API flows.
- Contract integration points with ABIs and transaction metadata handling.
- Local developer stack with Postgres + backend + frontend.

What is simplified or mocked for the hackathon:

- Validator governance and institutional onboarding rules are represented as configurable logic.
- Privacy and encrypted-transfer behavior is demonstrated through backend policy/encryption services, not full production cryptography infrastructure.
- Liquidity routing and bridge operations are represented as preparation/interop flow, not a production bridge deployment.
- Credit underwriting is rule-based and simplified, not external-bank integrated.

## Demo Instructions

### Prerequisites

- Node.js 20+
- pnpm 9+
- Docker Desktop

### 1) Start backend dependencies (Postgres)

From [aleph-back](aleph-back):

```bash
docker compose up -d db
```

### 2) Run backend API

From [aleph-back](aleph-back):

```bash
pnpm install
pnpm start:dev
```

Expected: backend running on `http://localhost:3000`.

### 3) Run frontend

From [aleph-front](aleph-front):

```bash
pnpm install
pnpm dev
```

Expected: frontend running on `http://localhost:3000` (or next available port if 3000 is busy).

### 4) Simulate the flow

1. Login as supplier role and create a procurement pool.
2. Login as retailer role and add commitments.
3. Trigger aggregation/structuring from supplier dashboard.
4. Execute tokenization path and inspect transaction/event logs.
5. Move lifecycle to funded, delivered, and repayment states.
6. Review history and status traces in dashboard/API output.

## Future Vision

- Integrate real financing partners (banks, distributors, fintech credit lines).
- Add dynamic credit scoring using repayment history and commerce data.
- Connect POS/ERP and distributor systems for automated order ingestion.
- Introduce production-grade privacy primitives for confidential institutional settlements.
- Expand cross-L1 liquidity rails for secondary financing markets.

## Team & Credits

Built during Avalanche hackathon by:

- Jeremy Aldama
- Contributors and mentors supporting the Aleph track submission

Special thanks to the Avalanche ecosystem and hackathon organizers for infrastructure and guidance.

---

For module-specific implementation details:

- Backend: [aleph-back/README.md](aleph-back/README.md)
- Frontend: [aleph-front/README.md](aleph-front/README.md)
