# Swap

Before swapping. you should obtain the estimated amount of the other token and ths swap routes.

There are two functions for this preperation.

* `sdk.Swap.estFromAmount`&#x20;
* `sdk.Swap.estToAmount`&#x20;

## Swap

use `sdk.Swap.swapTransactionPayload` method.

### Example

```typescript

const currencyAAmount = Math.pow(10,7)
const { amountOut: currencyBAmount, path: poolRoute} = await sdk.Swap.estToAmount({
  amountIn: currencyAAmount,
  from: "0xa",
  to: "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115"
})

const params = {
  // here must be fa type
  currencyA: '0xa',
  currencyB:
    "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
  currencyAAmount,
  currencyBAmount,
  slippage: 0.1,
  poolRoute,
  recipient: '',
}

const payload = await sdk.Swap.swapTransactionPayload(params)
console.log(payload)
```

