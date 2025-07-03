# Create pool

## 1. Create a pool with some initial liquidity to be added

use `sdk.pool.createPoolTransactionPayload` method.

### Function input params

* `currencyA`:  coin/fa type of currency token
* `currencyB`:  coin/fa type of currency token
* `currencyAAmount`: the amount about currency A, which used to add liquidity
* `currencyBAmount`: the amount about currency B, which used to add liquidity
* `feeTierIndex`: Fee Rate Tier will affect price precision. Now mainnet exist some different type FeeRateTier, the correspond to different fee rates.

{% include "../../../.gitbook/includes/feetiertable.md" %}

* `currentPriceTick` :  The tick corresponds to the current price.
* `tickLower` :  The tick corresponds to the lower price.
* `tickUpper` :  The tick corresponds to the upper price.

> - SDK provided a util function \`priceToTick\` for the calculation from price to tick.
> - -443636 < `tickLowerIndex` < currentPriceTickIndex<`tickUpperIndex` < 443636, 443636 is a constant, derived from the maximum range representable by the Q32.62 fixed-point number format.
> - Currently, creating a pool requires adding bidirectional liquidity.

* `slippage` :  slippage value. 0.1 means 0.1%

### Example

```typescript

import {
  FeeTierIndex,
  HighestTickByStep,
  LowestTickByStep,
  priceToTick,
} from "@hyperionxyz/sdk"

const currencyAAmount = Math.pow(10, 8);
// currencyA's decimals is 8
// currencyB's decimals is 6
const decimalsRatio = Math.pow(10, 8 - 6);
const feeTierIndex = FeeTierIndex["PER_0.05_SPACING_5"]

// To get the tick boundary of this feeTier
const lowerTick = LowestTickByStep[feeTierIndex];
const upperTick = HighestTickByStep[feeTierIndex];

// 1 -443630 443630
console.log(feeTierIndex, lowerTick, upperTick);

// Or To calculate tick by price
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
  currencyA: "0x1::aptos_coin::AptosCoin",
  currencyB:
    "0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T",
  currencyAAmount,
  currencyBAmount,
  feeTierIndex,
  currentPriceTick,
  tickLower,
  tickUpper,
  slippage: 0.1
};

// generate payload
const payload = await sdk.Pool.createPoolTransactionPayload(params)
// payload example
/*
{
  "function": "0xdd8d1a676801c6789fac9a06b8f6ced76f766c798f7e5ea276f25d80b9aa0af0::router_adapter::create_liquidity_entry",
  "typeArguments": [],
  "functionArguments": [
    // Token A FA type
    '0xa',
    // Token B FA type
    '0xb',
    // feeTierIndex: it can be found from the table above.
    1,
    // Pool Type: a constant value, just set it to false
    false,
    
    // the ticks must be greater and equal to 0
    // If you want to pass a negative integer, please convert it to a unsigned integer.
    // low price's tick
    22410,
    // high price's tick
    25930,
    // current price's tick
    22940,
    // Token A amount
    100000000,
    // Token B amount
    200287120,
    // Token A amount * (1 - slippage)
    99900000,
    // Token B amount * (1 - slippage)
    200086833,
    // Expiration time in second
    4891474469
  ]
}
*/

// or

/*
{
  "function": "0xdd8d1a676801c6789fac9a06b8f6ced76f766c798f7e5ea276f25d80b9aa0af0::router_adapter::create_liquidity_both_coin_entry",
  "typeArguments": [
     "0x1::aptos_coin::AptosCoin",
     "0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T"
   ],
  "functionArguments": [
    // feeTierIndex: it can be found from the table above.
    1,
    // Pool Type: a constant value, just set it to false
    false,
    
    // the ticks must be greater and equal to 0
    // If you want to pass a negative integer, please convert it to a unsigned integer.
    // low price's tick
    22410,
    // high price's tick
    25930,
    // current price's tick
    22940,
    // Token A amount
    100000000,
    // Token B amount
    200287120,
    // Token A amount * (1 - slippage)
    99900000,
    // Token B amount * (1 - slippage)
    200086833,
    // Expiration time in second
    4891474469
  ]
}
*/
```





{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
