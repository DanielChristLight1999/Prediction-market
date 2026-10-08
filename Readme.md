# DecentraPredict — Decentralized Prediction Market

> A full-stack prediction-market application combining a Next.js client, Node.js/Express API, MongoDB data layer, and an Anchor/Rust smart contract on Solana.

## Why this project is interesting
The project integrates three engineering layers: a web client, application/backend services, and on-chain market logic. It demonstrates work across conventional full-stack development and blockchain infrastructure.

## Features
- Create custom prediction markets
- Add liquidity
- Place token-based Yes/No bets
- Oracle-driven resolution
- Referral rewards
- User profiles and participation history
- Pending, active, and resolved market states
- Solana wallet integration

## Architecture
~~~text
Next.js / React
      │
      ▼
Node.js / Express API
   │            │
   ▼            ▼
MongoDB     Solana / Anchor
                 │
                 ▼
            Switchboard
~~~

## Technology
| Layer | Technology |
|---|---|
| Frontend | Next.js, React, TypeScript, Tailwind CSS |
| Backend | Node.js, Express, TypeScript |
| Database | MongoDB |
| Blockchain | Solana |
| Smart contract | Anchor 0.29 / Rust |
| Oracle | Switchboard |
| Wallet | Solana Wallet Adapter / Phantom |

## Market Lifecycle
~~~text
Create → Pending → Active → Resolution → Resolved
~~~

The application separates market participation from final resolution. Oracle data provides the external outcome required to resolve supported markets.

## Engineering Focus
### Full-stack boundaries
The project separates presentation, API/business logic, persistence, and on-chain execution.

### Blockchain integration
The backend contains a dedicated SDK/integration boundary for interacting with the prediction-market program.

### Oracle-based resolution
Oracle integration forms the reliability boundary between external information and on-chain resolution.

### Explicit market states
Pending, active, and resolved states provide clear rules for valid operations.

## Repository Structure
~~~text
BackEnd/                         API and blockchain integration
FrontEnd/                        Next.js application
prediction-market-smartcontract/ Anchor/Rust program and tests
~~~

## Local Development
~~~bash
cd prediction-market-smartcontract
anchor build
anchor test
~~~

~~~bash
cd BackEnd
npm install
npm run dev
~~~

~~~bash
cd FrontEnd
npm install
npm run dev
~~~

Do not commit real credentials, private keys, RPC secrets, or wallet signing material.

## Portfolio Context
This is one of Daniel Ngene's public examples of full-stack and blockchain engineering. Related proprietary prediction-market work is documented separately as a sanitized case study.

- [WHEN Markets case study](https://github.com/DanielChristLight1999/when-markets-case-study)
- [Portfolio](https://github.com/DanielChristLight1999/clight-portfolio)