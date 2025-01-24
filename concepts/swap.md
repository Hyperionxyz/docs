# Swap

Swaps are one of the most common interactions with a DEX. The mechanism of token swap is easy to understand, which is to sell the tokens that are currently owned by the swapper for the proportional amount of the destination tokens. In this process, a small percentage of swap fee will be deducted, which is the incentives to those liquidity providers.

The execution of swaps in the Hyperfluid protocol supports both AMM and Orderbook models. In the AMM model, swaps are executed against a passive liquidity pool, with liquidity providers earning transaction fees proportional to the active liquidity they contribute. Meanwhile, the Orderbook model follows a first-in-first-out policy, where order timing plays a crucial role in execution priority. This dual approach offers users flexibility, allowing them to choose between automated liquidity provision and direct market orders based on their trading strategy.

## **Price Impact** <a href="#price-impact" id="price-impact"></a>

In an order book market or a CEX, the price impact of an order depends on the size and array of the opening limit buy or sell orders. The final execution price of an order is usually the weighted average price of multiple limit orders.

The price impact in an AMM or in a concentrated liquidity protocol is sort of different. During the swap, the relative value of one token to the other changes dynamically and continuously so the final execution price of a swap lies somewhere between the start price and end price. The price impact for a swap order will be affected by the real-time available liquidity in corresponding price space. The price impact will be much smaller for a given swap size if the liquidity depth at the particular price is higher.

## **Slippage** <a href="#slippage" id="slippage"></a>

A swap user should have seen the term ‘slippage’ or ‘price slippage’ on a DEX before. That is the term that we use to describe the possible price change that may occur during a transaction is pending.

To respond to the possible price change, we adopt the concept of slippage tolerance. Slippage tolerance can be set by a user, which is to determine the largest price impact that the user is willing to accept. If the final execution price is outside of the acceptable slippage range, the transaction will get failed to protect the user’s interests.

A trade that uses assets and tokens that are purchased before paying for them. A trade that uses the tokens purchased before paying for them.
