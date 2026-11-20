# How to Submit & Requirements — Metric Bug Bounty

**Program**: Metric XYZ on Immunefi  
**Max Bounty**: $500,000 (Critical)  
**Submit here**: https://bugs.immunefi.com/dashboard/new-submission  
**Program page**: https://immunefi.com/bug-bounty/metric/

---

## What You Need to Win (Get Paid)

1. **Valid in-scope vulnerability** that matches one of the listed impacts on the Immunefi scope page.
2. **Runnable Proof of Concept (PoC)** — required for **all** severities.
3. The bug must not already be listed in their known issues or audit reports (Zellic / Sherlock).
4. Testing must be done on a **local fork**. Testing on mainnet or public testnet is prohibited.

### High-Value Impacts to Target
**Critical**:
- Direct theft of user funds
- Permanent freezing of funds
- Protocol insolvency
- Oracle accepting a price update without valid Pyth/Chainlink signature or unauthorized compressed-feed push

**High**:
- Bypassing admin fee caps or price-provider timelock
- Swap executing outside the band or beyond staleness limit on anchored pools
- Unauthorized use of protocol roles
- Theft or permanent freezing of unclaimed yield/royalties

---

## Submission Process

1. Create or log in to an Immunefi account.
2. Go to: **https://bugs.immunefi.com/dashboard/new-submission**
3. Select the **Metric** program.
4. If the issue is under Primacy of Impact, select the “Primacy of Impact” asset placeholder.
5. Fill in:
   - Clear, descriptive title
   - Detailed description of the vulnerability and real impact
   - Select all applicable impacts
   - Your EVM wallet address for payout (USDC on Ethereum)
   - Attach or link your **runnable PoC**
6. Submit.

### PoC Requirements
- Must be runnable as-is on a local fork.
- Clear and easy to follow (good variable names, comments recommended).
- Show the actual impact (funds stolen, frozen, incorrect price accepted, etc.).

---

## Rewards

| Severity | Reward |
|----------|--------|
| Critical | 20% of funds at risk (min $50,000 – max $500,000). Permanent freezing capped at $200,000 |
| High     | $10,000 – $50,000 |
| Medium   | $2,500 – $10,000 |
| Low      | $1,000 |

- Paid in **USDC on Ethereum**
- **No KYC** required
- Critical generally requires at least ~$10k funds directly at risk (otherwise max High)

---

## Important Rules

- Do **not** test on mainnet or public testnet.
- Do **not** disclose publicly until the issue is fixed and Metric/Immunefi approves (Category 3).
- Known issues from audits are out of scope: https://github.com/Metricxyz/Known_issues
- Rate limit on Immunefi: max 5 reports per 48 hours.

---

## Useful Links

- Immunefi Program: https://immunefi.com/bug-bounty/metric/
- Scope: https://immunefi.com/bug-bounty/metric/scope/
- Metric Docs: https://docs.metric.xyz/reference/bug-bounty
- Known Issues: https://github.com/Metricxyz/Known_issues
- Oracle Contracts: https://github.com/Metricxyz/oracle-contracts
- Periphery Contracts: https://github.com/Metricxyz/periphery-contracts
- Pool Contracts: https://github.com/Metricxyz/pool-contracts

---

**Last updated**: November 20, 2026
