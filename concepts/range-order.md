# Range Order

Powered by the concentrated liquidity algorithm, users can conveniently achieve a lot of advanced trading strategies that are infeasible in AMM DEXes.

By creating a liquidity position with a price range to be set to one side of the spot price, LPs can provide their liquidity with single-sided asset. This allows liquidity providers to simulate limit orders that are very common in those orderbook markets or CEX. The difference is that a limit order is created with a particular predetermined buy or sell price and the order may be filled at some point in the future, while a single-sided liquidity position order in concentrated liquidity protocol comes with a price range. When the spot price enters the preset range of the position, continuous token swap will be activated in the position. If the price has fully crossed the price range of the position, all original assets will be exchanged for the target assets which can be withdrawn by the LP to close the order. We call this type of order mode as range orders.

The roles who place range orders are liquidity providers instead of swappers, so they are regarded as makers who will earn fees when a range order is executed. By creating rational liquidity positions, LPs can easily buy at dips and sell at rallies like professional traders and earn transaction fees at the same time.

## **Order Types Supported by Range Order** <a href="#order-types-supported-by-range-order" id="order-types-supported-by-range-order"></a>

Although the range order trading is quite similar to limit orders in orderbook market, there are still certain differences due to the underlying mechanism of concentrated liquidity protocol. What can be supported by concentrated liquidity range order includes take-profit orders and buy-limit orders.

### **Take-Profit Orders**

For example, the current price of a BTC-USDC pool is 20,000 USDC/BTC and you want to sell your BTC for USDC when BTC price reaches 21,000 USDC/BTC. This is feasible by placing range orders because the price space above the current price is fully denominated in the higher-valued token in a concentrated liquidity pool. You can open a position with a narrow price range like 21,000-21,001 USDC/BTC and add your BTC into the pool. Your order will be filled if the price keeps increasing and crosses your liquidity position.

### **Buy-Limit Orders**

For example, the current price of the BTC-USDC pool is 20,000 USDC/BTC. You predict that the BTC price will rebound if it drops to 19,000, so you plan to buy some BTC with USDC at the price of 19,000. It can be achieved by range orders because the space below the current price is denominated in the lower-valued asset, USDC. You can simply create a position with a price range like 19,000-19,001 USDC/BTC. Your BTC will all be swapped into USDC when the spot price drops and crosses your position price range.

## **Position Management** <a href="#position-management" id="position-management"></a>

One thing to note is that to ensure your range order is completely filled, you need to withdraw your position assets in time after your position range is crossed in case that the spot price re-enters the price range. This can be handled manually or be managed with the help of a third-party position manager protocol that has integrated Hyperfluid’s smart contract.

Besides, it is up to liquidity providers on how to set the price range of a range order position. Setting a wider price interval may help you earn more transaction fees if price fluctuation is intense within your position range, while you need to bear a higher risk that your order cannot be completely filled if the price reserves before it crosses your full range.
