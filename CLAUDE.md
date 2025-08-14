## Product Overview

### Concept

au PAY In-App Wallet: A wallet integrated with au PAY that enables users to purchase cryptocurrencies in just a few taps using Ponta Points.

- Easy: Sign up instantly with only an email and passcode. From registration to first purchase takes just minutes.
- Valuable: Convert unused Ponta Points into cryptocurrencies such as BTC or USDC, starting from small amounts.
- Secure: Backed by KDDI-level security and safety alerts, with full Japanese-language support.

---

### Target Audience

- Primary Users: au PAY users with prior experience in point investments or NISA but new to cryptocurrency.
- Pain Points: Barriers such as complex account setup, KYC requirements, order-book trading complexity, and volatility concerns.
- Future Expansion: Add advanced features (e.g., swaps, DApp connectivity) to attract intermediate users.

---

### Value Proposition

| Item | Competitor 1: Domestic beginner exchange (e.g., Coincheck, bitFlyer) | Competitor 2: Major overseas crypto wallets | This Product | Note |
| --- | --- | --- | --- | --- |
| Registration Difficulty | △ High barrier: requires address, personal info, and KYC | ◎ Email + biometric/passcode only | ◎ Email + passcode only | Strong fit for target |
| Trading Convenience | △ Requires order-book trading; low fees but high withdrawals | × Cannot purchase directly in JPY | ○ Amount-based purchases without order book; higher fees acceptable when using points | Strong fit for target |
| Trust & Safety | ◎ Domestic legal protection | △ Mostly foreign-made, no Japanese support | ◎ KDDI brand + Japanese support | Strong fit for target |
| DApp Connectivity | △ Requires transfer to wallet | ◎ Direct connection possible | ○ Easy via WalletConnect | For future expansion |
| Supported Currencies | ○ Many purchase currencies, no swaps | ◎ No purchases, many swaps | ○ Fewer purchases, many swaps | For future expansion |

---

## User Journey

### Primary Flow

1. Enter via au PAY ecosystem landing page; see promotions like “Crypto with Points” or “Campaigns.”
2. Agree to terms + email registration + passcode setup → account created in 30 seconds.
3. View campaign banners on the home screen.
4. Tap “Exchange with Ponta Points”, enter amount, confirm transaction, purchase BTC.
5. Check portfolio value on the home screen.
6. Re-check portfolio value after several days.

---

### Use Cases

- Use leftover Ponta Points to buy BTC in small amounts via a simple JPY-based UI.
- Monitor asset balance daily.
- Swap purchased BTC in small amounts to try other cryptocurrencies.
- Connect to DApps via WalletConnect for lightweight Web3 experiences.

---

## Key KPIs (Tentative)

- Monthly points exchanged: ≥ 28M JPY
- Registration → first purchase conversion: ≥ 30%
- Median time to first purchase: ≤ 5 minutes
- D30 retention: ≥ 6%

---

## Scope

| Category | Feature | Initial Release | Future Scope |
| --- | --- | --- | --- |
| Core | Account creation/authentication | Full account lifecycle | – |
| Core | Multi-chain support | Ethereum, Polygon, Base, Aptos, Oasys | Additional EVM chains, Solana, Bitcoin |
| Core | FT display/send/receive | Only CoinGecko-supported FTs | Any token via custom addition |
| Core | NFT display/send/receive | Supports ERC721 & ERC1155 without explicit labeling | Support all major standards with labeling |
| Core | Wallet address display/copy | Display, QR, copy | – |
| Core | Transaction history | Points exchange, swap, charge, send | Add receive and external DApp activity |
| Core | WalletConnect | QR/URI connection | – |
| Core | Registration & login | Email + passcode | – |
| Core | Support contact | In-app link to external form | – |
| Core | Safe site filtering | Warn on non-whitelisted DApps | – |
| Core | Announcements | Campaign/news list | – |
| Core | Settings/links | Account info, history, safe site check, backup | Add gas fee adjustment, site list |
| Unique | Ponta Crypto Exchange | Buy cbBTC/USDC on Base with Ponta Points | – |
| Unique | Swap | Cross-chain swaps via 1inch API, 100–200 currencies | Add more pairs, Aptos swaps |
| Unique | Crypto charge | Charge au PAY balance with cbBTC/USDC (KYC users only, max 50k JPY/month) | – |
| Unique | au Wallet migration | – | Migration via recovery phrase |
| Unique | Passcode backup | Backup via au ID + phone number | – |

---

## UI/UX

Principles:

- Keep cognitive load low while showing essential investment info for beginners.
- Use familiar, beginner-friendly terminology.
- Hypotheses:
    - Screen transition speed is critical (inspired by Robinhood).
    - Small delight elements (e.g., confetti after trades, Ponta character) may increase engagement (inspired by Robinhood and Duolingo).

---

## Non-Functional Requirements

- Language: Japanese only
- Platforms: iOS, Android
- Performance: 99.9% uptime target, initial load < 2 sec
- Support: Japanese help, business-hour email support
- Compliance: Payment Services Act & Financial Instruments and Exchange Act

---

## MVP Hypotheses

- Point-based entry + lightweight registration → high first-purchase rate
- KDDI brand trust → higher spend and retention
- Amount-based UI satisfies beginners even with slightly higher fees

Risks:

- User acceptance of one-way flow: Ponta Points → crypto → au PAY charge
- Legal classification of Ponta crypto exchange, swaps, and charge under the Payment Services Act