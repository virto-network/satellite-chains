### **Project Overview**

**Kabocha** is a [satellite parachain](https://github.com/monsieurbulb/satellite-chains/tree/main) on Kusama, governed by $KAB token holders from the **Krievo parachain**, which is built on the [Virto node](https://github.com/virto-network/virto-node/) and uses KSM as its primary currency.

The network utilises the [Brale](https://brale.xyz) and Asset Hub issued dUSD stablecoin as a default payment mechanism. 

Kabocha’s launch project is **KIMCHI** - a simple, user-facing prediction market/app based around to Kusama (KSM) and Polkadot (DOT) token prices. The market is settled in dUSD and incorporates KAB rewards.

---

### **Technical Specification**

#### **1. Kabocha Parachain**
   - **Architecture**: Built as a Kusama satellite chain governed by Krievo with KAB as its native currency.
- **Distribution**: Forked from [Edgeware](https://forum.polkadot.network/t/re-introducing-edgeware-substrates-most-chaotic-governance-experiment-and-second-oldest-mainnet/500) to enable broad, fair and aligned genesis. [W3F](https://web3.foundation/) have large stake representing their contributions but not controlling share.
- **USP**: Restructures base economic incentives through governance mediated separation of powers to ensure long term network alignment with the aim of advancing, rather than collapsing collective intelligence. 

   - **Core Functions**:
      - **Cross-Chain Governance**: Kabocha defers decisionmaking to a Krievo based organisation governed via KAB token holdings allowing for integrated voting and proposal mechanisms.
      - **Interoperability with dUSD stablecoin**: dUSD will be the main currency within Kabocha for payments providing stability and ease for users.
      - **Parachain Governance**: Kabocha's Krievo org maintains root permissions over the Satellite chain, enabling cross-chain upgrades, proposals and decisionmaking.

   - **Primary Pallet**:
      - **Asset management**: Kabocha's network token KAB is minted on the Satellite chain via the `Assets Pallet`.
      - **Minting and Rewards**: $KAB is awarded via [`Pallet Mint with Fee`](https://github.com/kabocha-network/pallet_mint_with_fee) in return for projects delivering objective on-chain impact allowing for automated performance related incentives.
      - **Stablecoin Integration**: Launches with Asset Hub integration for dUSD issuance, can migrate to Kabocha Assets Pallet as/when necessary.

#### **KIMCHI**
It’s a bet. A simple, clean, high-stakes call on whether Kusama (KSM) can close the gap on Polkadot (DOT). If you’re tired of safe plays and ready to see KSM punch above its weight, welcome to KIMCHI. LFG.
   - **Design**:
      - **Oracle Pallet**: Maintains real-time DOT/KSM ratios and updates KIMCHI’s value, with both native and dUSD-converted values.
        
   - **Smart contract**:
      - **createBet(amount: dUSD, direction: string, duration: uint256)**: Initiates a bet on KSM vs. DOT price movement.
      - **checkOutcome(betId: uint256)**: Verifies the bet's outcome based on current prices.
    - **distributePayout(betId: uint256)**: Automatically transfers winnings to the user's wallet.

   - **Price Oracle Integration**:
      - Use reliable oracles for real-time KSM and DOT price feeds.

   - **User Interface**:
      - Dashboard for tracking bets, market prices, and payouts.
