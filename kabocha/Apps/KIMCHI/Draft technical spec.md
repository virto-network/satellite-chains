### **Technical Specification: KIMCHI Mint, Burn, and Redemption System (DRAFT)** 

The following design combines algorithmic adjustments, oracle-based pricing, and community-driven governance with the aim of stabilising KIMCHI around the KSM/DOT ratio, supporting a dynamic and resilient token model inspired by algorithmic stablecoins.

#### **1. Overview and Objective**
   - The KIMCHI token's supply dynamically expands or contracts based on the real-time **KSM/DOT price ratio**, aiming to maintain its value in alignment with this ratio.
   - KIMCHI functions as both a speculative asset and a price-tracking token, balancing supply based on buy/sell demand to prevent significant divergence from the KSM/DOT ratio.
   - 
---

### **2. Core Components**

#### **Oracle-Powered Pricing Mechanism**
   - **Price Oracle Integration**: Use a secure oracle/s (e.g., Chainlink) to fetch the latest DOT/KSM price ratio at regular intervals.
   - **Target Price Calculation**: Set KIMCHI’s target price as **1:1 with the DOT/KSM ratio**. This price updates with each oracle update, setting the standard against which minting and burning adjustments are made.

#### **3. Minting and Supply Expansion**
   - **Mint Functionality**: When users purchase KIMCHI, new tokens are minted at the target price defined by the DOT/KSM ratio.
      - **Condition**: KIMCHI’s market price must exceed the target price, indicating demand exceeds supply.
   - **Dynamic Minting Rate**: The minting rate can increase based on buy volume. A simple formula:
     \[
     \text{Mint Rate} = \text{Base Rate} \times \left(1 + \frac{\text{Current Price} - \text{Target Price}}{\text{Target Price}}\right)
     \]
      - **Purpose**: Prevents significant price divergence by rapidly expanding supply when demand is high.

#### **4. Burning and Supply Contraction**
   - **Burn Functionality**: Tokens are burned when users sell KIMCHI, reducing supply to support the price.
      - **Condition**: KIMCHI’s market price falls below the target price, indicating supply exceeds demand.
   - **Dynamic Burn Rate**: Adjust burn rate according to sell volume. A potential formula:
     \[
     \text{Burn Rate} = \text{Base Rate} \times \left(1 + \frac{\text{Target Price} - \text{Current Price}}{\text{Target Price}}\right)
     \]
      - **Purpose**: Stabilizes KIMCHI’s value by decreasing supply when demand wanes.

#### **5. Redemption Mechanism**
   - **Redemption Pool**: Create a dedicated pool where users can redeem KIMCHI for underlying assets (e.g., dUSD or DOT/KSM pairs).
   - **Redemption Rate**: Offer redemptions at a discounted or premium rate, based on the KIMCHI price divergence:
      - **Above Target**: Redemption at a slight premium incentivises selling to stabilise price.
      - **Below Target**: Redemption at a discount encourages buybacks, stabilising price via demand.
   - **Reserve Assets**: dUSD and/or KSM/DOT pairs in the redemption pool back redemptions, ensuring stability and supporting liquidity.

#### **6. Algorithmic Adjustments Inspired by Stablecoins**
   - **Expansion Incentives**: To manage excess demand, offer small minting bonuses when KIMCHI trades above the target.
   - **Contraction Penalties**: When KIMCHI trades below target, add a small redemption penalty to incentivise holding and discourage excessive selling.

---

### **7. Security and Stability Mechanisms**

- **Circuit Breakers**: Implement safety controls that halt minting/burning if KIMCHI’s price diverges more than 20% from the target, allowing for market correction and avoiding excess volatility.
- **Oracle Fail-Safes**: Set backup price feeds and fallback protocols if the primary oracle fails, freezing minting/burning if no reliable price data is available.

---

### **8. Governance Controls**

- **Community Voting**: Enable KIMCHI holders to vote on adjustments to minting/burning rates, redemption parameters, or oracle updates, aligning the system’s behavior with the community’s preferences.
- **Automated Updates**: Establish governance-initiated updates, with parameters reset periodically based on current market trends or community input.
