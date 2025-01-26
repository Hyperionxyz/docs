# Add Liquidity

Once you have set a suitable tick range, you can proceed to add liquidity to this position. The quantity composition of tokens you need to add is affected by the current price of the pool and the tick interval you have chosen.



## 1. Create the payload of Add Liquidity&#x20;

use `sdk.Position.addLiquidityTransactionPayload` method

### Function Input params

* `positionId` : The position id.
* `currencyA`:  coin/fa type of currency token
* `currencyB`:  coin/fa type of currency token
* `currencyAAmount`: the amount about currency A, which used to add liquidity
* `currencyBAmount`: the amount about currency B, which used to add liquidity
* `feeRateTier`: Fee Rate Tier will affect price precision. Now mainnet exist some different type FeeRateTier, the correspond to different fee rates.

{% include "../../../.gitbook/includes/feetiertable.md" %}

* `slippage` : slippage value. 0.1 means 0.1%.

### Example

```typescript


const currencyAAmount = Math.pow(10, 8);
// currencyA's decimals is 8
// currencyB's decimals is 6
const decimalsRatio = Math.pow(10, 8 - 6);
const feeTierIndex = FeeTierIndex["PER_0.05_SPACING_5"]

const currentPriceTick = priceToTick({
  price: 995,
  feeTierIndex,
  decimalsRatio,
})

const tickLower = priceToTick({
  price: 992,
  feeTierIndex,
  decimalsRatio,
})

const tickUpper = priceToTick({
  price: 1336,
  feeTierIndex,
  decimalsRatio,
})

const [_, currencyBAmount] = await sdk.Pool.estCurrencyBAmountFromA({
  // address here mus be fa type
  currencyA: "0xa",
  currencyB:
    "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
  currencyAAmount,
  feeTierIndex,
  tickLower,
  tickUpper,
  currentPriceTick,
});

const params = {
    positionId: '',
    currencyA: "0x1::aptos_coin::AptosCoin",
    currencyB:
      "0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T",
    currencyAAmount,
    currencyBAmount,
    slippage: 0.1,
    feeTierIndex,
}

const payload = await sdk.Position.addLiquidityTransactionPayload(params)

const { hash } = await AptosClient.submitAndSignTransaction({
  data: payload
})
```







