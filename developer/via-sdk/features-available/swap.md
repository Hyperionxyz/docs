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
  amount: currencyAAmount,
  from: "0xa",
  to: "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
  // safeMode
  // if safeMode is true, only few swap token pairs will return path route
  // default: true. support from (v0.0.12)
  safeMode: false
})

/*
{
  
  "amountOut": "10000000", // This is for toAmount
  "amountIn": "1279371", // This is for fromAmount
  
  // swap path route
  "path": [
    "0x0d21c2f5628db619957703e90ab07bcb2b13ad6983da2b5d721f24523cae29ff"
  ]
}
*/

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



## Swap with partnership

use `sdk.Swap.swapWithPartnershipTransactionPayload` method.

### Example

```typescript

const currencyAAmount = Math.pow(10,7)
const { amountOut: currencyBAmount, path: poolRoute} = await sdk.Swap.estToAmount({
  amount: currencyAAmount,
  from: "0xa",
  to: "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
  // safeMode
  // if safeMode is true, only few swap token pairs will return path route
  // default: true. support from (v0.0.12)
  safeMode: false
})

/*
{
  
  "amountOut": "10000000", // This is for toAmount
  "amountIn": "1279371", // This is for fromAmount
  
  // swap path route
  "path": [
    "0x0d21c2f5628db619957703e90ab07bcb2b13ad6983da2b5d721f24523cae29ff"
  ]
}
*/

const params = {
  // here must be fa type
  currencyA: '0xa',
  currencyB:
    '0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115',
  currencyAAmount,
  currencyBAmount,
  slippage: 0.1,
  poolRoute,
  partnership: 'your_platform_name'
}

const payload = await sdk.Swap.swapWithPartnershipTransactionPayload(params)
console.log(payload)
```

{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
