# SqrtLiquidityICO

## **Overview**

The SqrtLiquidityICO smart contract is designed to create a fair and dynamic ICO mechanism by leveraging a liquidity pool model similar to those used in DeFi platforms. This contract allows participants to deposit dual tokens (e.g., WBTC and USD) and calculates their share of ICO tokens based on the sqrt(k) model. Key mechanisms include a time-based linear interpolation to reduce the maximum allowable units (maxUnits) over the ICO duration and dynamic share allocation based on token deposits.

## **Key Mechanisms**

1. **Time-Based Max Unit Reduction**
   - **Initial Max Units**: At the start of the ICO, the maxUnits are set high, encouraging early participation by allowing participants to acquire larger shares.
   - **Linear Decrease Over Time**: As time progresses, the maxUnits linearly decrease according to a pre-set duration. This mechanism limits the number of shares that can be acquired later in the ICO, incentivizing earlier deposits.
   - **Final Max Units**: By the end of the ICO, the maxUnits reach a lower limit, making it increasingly difficult for late participants to acquire significant shares.

2. **Dynamic Share Allocation Using Sqrt(k)**
   - **Dual Token Deposits**: Participants can deposit either or both types of tokens, allowing flexibility and encouraging diverse participation.
   - **Sqrt(k) Calculation**: The share allocation is based on the liquidity within the pool and the sqrt(k) model, where \( k \) is the product of the reserves of the two tokens. The change in sqrt(k) determines the participant's share:
     - **Example**: If a participant deposits tokens, the new reserves are used to calculate a new \( k \) value. The increase in sqrt(k) from the previous value determines the participant’s share.
   - **Impact of Token Type**: The value of the deposited tokens relative to the existing pool affects the share. Depositing a lower-priced token results in a smaller share increase compared to a higher-priced token.

## **Comparison with Traditional Dutch ICOs**

1. **Pricing Mechanism**
   - **Traditional Dutch ICO**: Prices decrease over time until all tokens are sold or the minimum price is reached. Participants choose when to buy based on their price expectations.
   - **SqrtLiquidityICO**: Uses a liquidity pool model where the price is dynamically determined by the pool's reserves and the sqrt(k) function.

2. **Participation and Share Calculation**
   - **Traditional Dutch ICO**: Participants purchase tokens directly at a given price, with the number of tokens determined by the purchase amount and current price.
   - **SqrtLiquidityICO**: Participants deposit tokens into a pool, and their shares are determined by the change in sqrt(k) caused by their deposits.

3. **Max Unit Limitation**
   - **Traditional Dutch ICO**: Typically, there is no restriction on the number of tokens a participant can purchase other than the total supply and price.
   - **SqrtLiquidityICO**: Implements a time-based reduction of maxUnits, incentivizing early participation by allowing larger shares initially and gradually limiting the shares available to later participants.

## **Summary**

The SqrtLiquidityICO smart contract combines the principles of DeFi liquidity pools with a fair and balanced ICO mechanism. By using the sqrt(k) model and implementing a time-based reduction of maxUnits, it ensures equitable token distribution, minimizes the impact of large deposits, and incentivizes timely participation. This dynamic approach creates an inclusive and market-driven ICO environment, differing from traditional Dutch ICOs by providing a more balanced and fair distribution of tokens based on liquidity contributions.
