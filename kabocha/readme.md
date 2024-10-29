### **Project Overview**

**Kabocha** is a [satellite parachain](https://github.com/monsieurbulb/satellite-chains/tree/main) on Kusama, governed by $KAB token holders from the **Krievo parachain**, which is built on the [Virto node](https://github.com/virto-network/virto-node/). 

The network utilises the [Brale](https://brale.xyz) and Asset Hub issued dUSD stablecoin as a default payment mechanism. 

Kabocha’s launch project is **KIMCHI** - a speculative token and user-facing prediction market/app, offering dynamic exposure to the Kusama (KSM) and Polkadot (DOT) price ratio alongside KAB rewards.

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
It’s not just a token. It’s a bet. A simple, clean, high-stakes call on whether Kusama (KSM) can close the gap on Polkadot (DOT). If you’re tired of safe plays and ready to see KSM punch above its weight, welcome to KIMCHI. LFG.
   - **Design**:
      - **Oracle Pallet**: Maintains real-time DOT/KSM ratios and updates KIMCHI’s value, with both native and dUSD-converted values.
      - **DEX**: Possibly uses`KSM FUN pallet` - combining `Assets Pallet` and `Asset Conversion Pallet` to enable launch of KIMCHI token and onboard selected pairs, bridged from Kusama to Polkadot to provide access to both $KSM and $DOT liquidity.
   - **Tokenomics**:
      - **DOT/KSM Ratio Pegging**: KIMCHI’s value relies on the DOT/KSM price ratio, allowing users to speculate on Kusama’s potential to catch up with Polkadot.
      - **Minting/Burning Logic**: The supply adjusts as users buy or sell. 
      - **KAB Rewards**: All transactions receive KAB via automated minting.

   - **User-Facing Application**:
      - **Wallet and dUSD Integration**: Supports a dUSD wallet, facilitating transactions and staking within Kabocha.
      - **Real-Time Dashboard**: Displays KIMCHI’s value in native terms and dUSD, tracks affiliate performance, and provides staking insights.

