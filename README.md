# MCORE-MAIL-001 | Sovereign Email Gateway

**Status:** OPERATIONALLY VERIFIED (Primary Scope)  
**Cost:** $0.00 / month  
**Authority:** AIS (MCORE-FDR-AIS-001)  
**Date:** October 21, 2026

## 1. Executive Summary
The MCore Sovereign Email Gateway is a zero-cost, highly secure inbound email routing architecture. It utilizes Cloudflare Email Routing to catch emails for custom domains and forward them to a secure, hidden master Gmail inbox without exposing the destination to the public internet.

## 2. Current Deployment (Dynamic Status)
The deployment has been locked to the **Primary Scope** for stability and verification.
- **Active Domains:** `mcoreai.com`, `meticulouscore.dev`, `meticulouscore.net`
- **Active Aliases:** `admin@`, `founder@`, `security@` (9 rules total)
- **Destination:** `meticulouscore@gmail.com` (Verified)
- **DNS Security:** 
  - MX: Cloudflare Routing
  - SPF: `v=spf1 include:_spf.mx.cloudflare.net ~all` (Softfail, Cloudflare authorized)
  - DMARC: `v=DMARC1; p=none; rua=mailto:dmarc@mcoreai.com;` (Monitoring mode)
  - DKIM/TLS-RPT: Enabled

## 3. Architecture & Code
- **Worker:** `mcore-mail-gateway` (Deployed, currently bypassed by explicit rules).
- **Repository:** [aminul-du/mcore-mail-001](https://github.com/aminul-du/mcore-mail-001)
- **Documentation Site:** `docs/index.html` (Ready for Cloudflare Pages deployment).

## 4. Immediate Next Steps
1. **Outbound Email:** Configure Gmail "Send mail as" to reply from `admin@mcoreai.com`.
2. **Scale to 15 Domains:** When ready, authorize the Cloudflare AI to replace the 9 explicit rules with the `mcore-mail-gateway` Worker catch-all.
3. **Documentation Site:** Deploy `docs/` via Cloudflare Pages.
