# DecentraPredict Architecture

## System Boundary

The application is divided into a web client, backend services, persistent application data, and an on-chain Solana program.

~~~text
Next.js / React
      │
      ▼
Express / TypeScript API
   │            │
   ▼            ▼
MongoDB      Solana SDK
                 │
                 ▼
          Anchor Program
                 │
                 ▼
           Oracle Layer
~~~

## Market Lifecycle

`Pending → Active → Resolved`

Pending markets can receive liquidity until the configured activation condition is satisfied. Active markets accept participation until their lifecycle closes. Resolution uses oracle information to determine the final outcome.

## Separation of Responsibilities

| Component | Responsibility |
|---|---|
| Frontend | User experience, wallet interaction, market presentation |
| Backend | API workflows, persistence, referral/profile services, chain integration |
| MongoDB | Application-oriented data |
| Solana program | On-chain market state and state transitions |
| Oracle | External outcome data used for resolution |

## Engineering Boundary

The backend's dedicated prediction-market SDK boundary keeps blockchain-specific operations from being scattered throughout API controllers and frontend components.

This makes the system easier to reason about and gives the frontend a conventional application API while preserving direct blockchain capabilities where required.