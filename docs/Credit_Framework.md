---
title: TR Score Idea

---

**Trustless Score Idealization**

To bridge the gap between traditional banking credit assessments and the decentralized world of cryptocurrencies, we can develop a comprehensive credit scoring framework for crypto addresses. This system aims to evaluate the creditworthiness of an address based on on-chain data, mirroring the factors banks consider when assessing individual credit scores.

Here is the proposed framework for such system with the tech debt that will entail.

---

### **The C.R.E.D.I.T. Score**

The C.R.E.D.I.T. Score is a 100-point system that evaluates a crypto address across six key dimensions:

1. **Collateral (25 points)**
2. **Repayment History (25 points)**
3. **Engagement (15 points)**
4. **Diversity of Assets (10 points)**
5. **Identity Verification (15 points)**
6. **Time in Network (10 points)**

---

#### **1. Collateral (25 Points)**

**Interpretation:** This dimension assesses the financial strength of an address by evaluating the value and quality of assets that can be used as collateral.

**Indicators:**

- **Total Asset Value:** The USD equivalent of all assets held in the address.
(For prototype we can scan asset on BSC for now)

- **Liquidity of Assets:** Proportion of assets that are easily convertible to cash (e.g., stablecoins, top-tier cryptocurrencies).
(When looking at Asset, we will give stablecoins a higher weight to this score following by bluechip coin ETH, BTC)

- **Collateralization (LTV) Ratio:** The ratio of collateral value to the amount borrowed on DeFi platforms.
(Need to look at multiple lending protocol and scan their collateral token to define this)

**->  Tech Debt for Collateral Part :**

- Asset scannning 
- Total Asset Value on Chain 
- Categorize on-chain asset type and define weight to them 
- Understand the top on chain lending protocol and define their what token is being used as collateral token and determine their conversion rate (how much ETH is being deposit correspond to how much lama-ETH that got back from the protocal) This is protocol based and suspect that this is a case by case rate.


---

#### **2. Repayment History (25 Points)**

**Interpretation:** This dimension examines the address's history of fulfilling financial obligations, similar to payment history in traditional credit scoring. However, since most of lending protocols are using overcollaterize model, we can only fault them if we can detect liquidation and debt utilization as debt repayment is handle by protocol conversion rate (token-collaterized token)

**Indicators:**

- **Default Instances:** Number of times the address has defaulted or been liquidated.
- **Debt Utilization:** The proportion of credit used relative to the total available credit.

**->  Tech Debt for Repayment Part :**

- Find out what happened when an address is being liqudated on a lending-leveraging platform (for instance we can try getting liquidated on purpose on https://www.alpacafinance.org/ and see)
- Token - Collaterized Token Ratio and calculate how much money is being leveraged on yield farming or others usages. (Hard)

---

#### **3. Engagement (15 Points)**

**Interpretation:** Measures the address's active participation in the crypto ecosystem, indicating experience and reliability.

**Indicators:**

- **Active Days/Months:** Number of days or months with at least one transaction.
- **Transaction Frequency:** Average number of transactions per week or month.
- **Total Protocol Usage:** Number of different DeFi platforms interacted with, especially lending and borrowing services.
- **Healthy Smart Contract Interactions:** Engagement with healthy smart contracts, showing advanced usage.
- **Blacklist Contract Interactions:** Engagement with money laundering/privacy smart contracts (this can be use as a minus point)
- **Compromised Contract Interactions:** Engagement with compromised smart contracts (this can be use as a minus point)

**->  Tech Debt for Engagement Part :**

- Find all of the popular lending and borrowing Defi platform for each of the network that we aim to score on
- Hard code smart contract address ???
- How should we black list smart contract ??
- How compromised smart contract will be updated in the system.

---

#### **4. Diversification Risk - Behavior Framework Scoring !! (10 Points)**

**Interpretation:** Assesses the address's asset diversification, reflecting sound investment strategies and risk management.

**Indicators:**

- **Asset Classes:** Variety of asset types held (e.g., cryptocurrencies, tokens, NFTs).
- **Cross-Chain Holdings:** Assets held across multiple blockchain networks.

**->  Tech Debt for Diversity Part :**

- This is the hardest to give a hard code rule for !!! even though it is easy to implement

---

#### **5. Identity Verification (15 Points)**

**Interpretation:** Establishes the credibility of the address through identity proofs and reputation systems.

**Indicators:**

- **KYC/AML Compliance:** Completion of Know Your Customer (KYC) and Anti-Money Laundering (AML) checks on reputable platforms.
- **Decentralized Identifiers (DIDs):** Ownership of verified decentralized identities like ENS domains or Lens Protocol profiles.
- **Social Proofs:** Verification through social platforms linked to the address.

**->  Tech Debt for Identity Part :**

- All this layer is already a tech debt in module planning
- Allocating weight for each of the identitity layers

---

#### **6. Time in Network (10 Points)**

**Interpretation:** Considers the longevity and consistency of the address's activity in the blockchain network.

**Indicators:**

- **Account Age:** Duration since the first recorded transaction.
- **Historical Participation:** Early involvement in significant network events or protocols.


**->  Tech Debt for Time Part :**

- Age is easy to do
- Historical Participation entails we know what has,is and will happen on chain ( What airdrops, genesis event, reward for testing protocal, ....)

---

### **Total Score: 100 Points**

Each dimension contributes to a comprehensive view of the address's creditworthiness, similar to how traditional banks assess individual credit scores.

---

### **Next step**

After agreeing on the above idealization, tasks can be handle to each team members in Data/Computation team to start on the technical debt described.

## Further study:

- [ AI and Machine Learning Framework for Robust Sybil Resistance](https://medium.com/@trustalabs.ai/trustas-ai-and-machine-learning-framework-for-robust-sybil-resistance-in-airdrops-ba17059ec5b7)
- [Proof of Innocence Program](https://medium.com/@trustalabs.ai/trustas-proof-of-innocence-program-fighting-back-against-poisoning-675db7c5e14b)

## References:

- [Trustalab Docs](:https://trusta-labs.gitbook.io/trustalabs/)