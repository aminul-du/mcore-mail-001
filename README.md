# MCORE-MAIL-001 | Sovereign Email Gateway

**Status:** PRIMARY SCOPE OPERATIONALLY VERIFIED  
**Cost:** $0.00 / month  
**Authority:** AIS (MCORE-FDR-AIS-001)  
**Target Scale:** 15 MCore Domains  

## 1. System Architecture

This repository manages the zero-cost, highly secure inbound email routing infrastructure for the MCore ecosystem. 

The architecture utilizes **Cloudflare Email Routing** to catch inbound mail for MCore domains and routes it securely to a hidden, verified master **Gmail** inbox (`meticulouscore@gmail.com`). The destination address is never exposed in DNS or public routing rules. 

A custom Cloudflare Worker (`mcore-mail-gateway`) is deployed and on standby to handle the future **15-zone catch-all** migration when the scope is unlocked.

## 2. Domain Matrix

The deployment is currently locked to the **Primary Scope** for stability and verification.

### Primary Scope (Active)
| Domain | Routing Status | Active Aliases | Destination Inbox |
| :--- | :--- | :--- | :--- |
| `mcoreai.com` | ✅ Live (Explicit Rules) | admin@, founder@, security@ | meticulouscore@gmail.com |
| `meticulouscore.dev` | ✅ Live (Explicit Rules) | admin@, founder@, security@ | meticulouscore@gmail.com |
| `meticulouscore.net` | ✅ Live (Explicit Rules) | admin@, founder@, security@ | meticulouscore@gmail.com |

### Extended Scope (Deferred)
| Domain | Routing Status | Destination Inbox |
| :--- | :--- | :--- |
| `mcore360.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoreacademy.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoreai.cloud` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoreai.dev` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoremesh.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoredns.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcorefabric.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoreshield.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcoreprime.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `mcorecare.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `kotlinbrain.com` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |
| `shorborno.ai` | ⏸️ DNS Ready (No Rules) | meticulouscore@gmail.com |

## 3. Recovery & Access

In the event of an emergency rebuild, the following access points are required. **Do not commit secrets to this repository.**

*   **Cloudflare Access:** Cloudflare Dashboard → API Tokens. Required scopes: `Zone.DNS:Edit`, `Zone.Email Routing Rules:Edit`, `Account.Workers Scripts:Edit`.
*   **Destination Inbox Access:** Google Account (`meticulouscore@gmail.com`) → Security → 2-Step Verification → **App Passwords**.
*   **Infrastructure Documentation:** Detailed deployment logs and DNS configuration are located in `docs/MCORE-MAIL-001-DEPLOYMENT.md`.
