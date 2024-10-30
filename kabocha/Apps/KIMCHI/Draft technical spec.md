### KIMCHI Protocol: Technical Specification

#### Overview
KIMCHI is an incentivised prediction market enabling users to bet on the relative performance of Kusama (KSM) against Polkadot (DOT), with payouts settled in dUSD. Users also receive 2% cashback in KAB on each trade, enhancing the incentive to participate. The protocol utilises smart contracts through the Krievo frontier pallet for seamless bet management and settlement.

---

### 1. **Smart Contract Functions**
The KIMCHI protocol will incorporate the following core functions:

- **createBet(amount: dUSD, duration: uint256, direction: string)**:
  - Initiates a new bet on KSM vs. DOT.
  - **Parameters**:
    - `amount`: Wager amount in dUSD.
    - `duration`: Time period for the bet.
    - `direction`: Indicates if the user bets on KSM outperforming DOT.
  - **Cashback**: Users receive 2% of the bet amount as KAB.

- **checkOutcome(betId: uint256)**:
  - Validates the outcome of the bet using real-time price data from oracles.

- **settleBet(betId: uint256)**:
  - Automatically distributes winnings or losses in dUSD at the end of the betting period, including the cashback reward.

- **mintWithFee(amount: uint256, fee: uint256)**:
  - Utilises the `pallet_mint_with_fee` to mint KAB as cashback for users.

---

### 2. **Price Oracles**
The protocol will integrate reliable price oracles to provide real-time price feeds for KSM and DOT, essential for determining bet outcomes.

---

### 3. **Example Solidity-like Code Reference**
Here's a simplified code snippet representing the KIMCHI smart contract functions, including the minting functionality:

```solidity
pragma solidity ^0.8.0;

import "./pallet_mint_with_fee.sol";

contract KIMCHI {
    struct Bet {
        address bettor;
        uint256 amount;
        uint256 duration;
        string direction;
        uint256 creationTime;
        bool settled;
    }

    mapping(uint256 => Bet) public bets;
    uint256 public betCount;

    function createBet(uint256 _amount, uint256 _duration, string memory _direction) public {
        require(_amount > 0, "Amount must be greater than 0");
        betCount++;
        uint256 cashback = (_amount * 2) / 100; // 2% cashback
        bets[betCount] = Bet(msg.sender, _amount, _duration, _direction, block.timestamp, false);
        
        // Mint cashback in KAB using the mintWithFee function
        mintWithFee(cashback, 0); // Fee can be adjusted as needed
    }

    function checkOutcome(uint256 betId) public view returns (string memory) {
        // Logic to retrieve price from oracle and determine outcome
    }

    function settleBet(uint256 betId) public {
        // Logic to settle the bet and transfer dUSD based on outcome
        // Include cashback logic in the settlement process
    }

    function mintWithFee(uint256 amount, uint256 fee) internal {
        // Call the mint function from the pallet_mint_with_fee
    }
}
```

---

### 4. **User Experience Flow**
1. **Bet Creation**: Users place bets on KSM vs. DOT using the `createBet` function, receiving 2% cashback in KAB.
2. **Monitoring**: Users can track their bets and market prices via a dashboard.
3. **Settlement**: At the end of the betting duration, users' bets are settled automatically in dUSD, and cashback in KAB is distributed accordingly.
