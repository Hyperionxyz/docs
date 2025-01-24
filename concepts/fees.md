# Fees

## **Swap Fees** <a href="#swap-fees" id="swap-fees"></a>

In our concentrated liquidity protocol, swap fees will be distributed proportionally to all in-range liquidity at the time of the swap transaction. Only the liquidity positions with price ranges that the current spot price lies in have provided liquidity, and therefore become entitled to earn fees. If the price exits a position’s range, the position will be switched to inactive status and no fees can be earned.

Unlike the common AMM contract which will automatically accrue new swap fees into the liquidity pool, in a concentrated liquidity protocol, swap fees are accumulated separately and liquidity providers can claim their fee earnings without withdrawing their liquidity.

It is important to reiterate that the Hyperfluid protocol simply comprises a set of autonomous smart contracts deployed on Aptos, operated directly by users calling functions on it (which allows them to interact with other users and/or pool their own selected assets in a multi-party peer-to-peer manner). There is no further control by or interaction with the original entity which had deployed the smart contract, which entity solely functions as a provider of technical tools for users, and is not offering any sort of securities product or regulated service nor does it hold any user assets in custody.

## **Fee Tiers** <a href="#fee-tiers" id="fee-tiers"></a>

In our concentrated liquidity protocol, we can set up multiple pools for the same token pair with different fee tiers. Initially, there will be 4 tiers that are allowed by the protocol: 0.01%, 0.05%, 0.25%, 1%.

The setting of multiple fee tiers can better satisfy the needs of different kinds of trading pairs. It also encourages the market to naturally find the most ideal liquidity distribution plan by itself. This gives much more flexibility to both liquidity providers and swappers.

It is reasonable to anticipate that different types of token pairs tend to progress towards particular fee levels according to their asset characteristics and the game between supply and demand from liquidity providers and traders. Assets with low volatility like stablecoins will be more likely to congregate in a pool with the lowest fee tier because it is less risky for LPs to hold these assets and most traders expect their transactions to be executed as close to 1:1 as possible. On the other hand, assets that are rarely traded may gravitate towards a higher fee as liquidity providers are bearing higher risks of holding such high-volatility assets.

## **Protocol Fees** <a href="#protocol-fees" id="protocol-fees"></a>

To maintain a healthy economic model that is beneficial to the project's sustainable project treasury for its long term development, a certain percentage (20% by default) will be taken from swap fees of every transaction on Hyperfluid as the protocol fee.
