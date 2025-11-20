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



## Swap with Partnership

use `sdk.Swap.swapWithPartnershipTransactionPayload` method.

(from v0.0.17)

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



## Swap via Aggregator

(from v0.0.24)

```typescript
// if from === input, est to token amount by from token amount 
// if to === input,  est from token amount by to token amount
const params = {
  amount: Math.pow(10,7),
  from: '0xa',
  input: '0xa',
  to: '0x357b0b74bc833e95a115ad22604854d6b0fca151cecd94111770e5d6ffc9dc2b',
  slippage: args.slippage,   // 0.1
};

// 1. est amount and get aggregation info
const aggregatorRoutes = await HyperionSDK.Swap.estAmountByAggregateSwap(params);
/*
{
  "fromToken": {
    "address": "0x000000000000000000000000000000000000000000000000000000000000000a"
  },
  "toToken": {
    "address": "0x357b0b74bc833e95a115ad22604854d6b0fca151cecd94111770e5d6ffc9dc2b"
  },
  // est amount
  // from -> to: true
  // to -> from : false
  "exactIn": true,
  "feeAmount": "50000",
  "fromTokenAmount": "100000000",
  "minToTokenAmount": "3217167",
  "toTokenAmount": "3249664",
  "quotes": {
    "route": [
      {
        "amountIn": "100000000",
        "amountOut": "3249664",
        "percentage": 100,
        "feeAmount": "50000",
        "routeTaken": [
          {
            "fromToken": {
              "tokenType": "0x000000000000000000000000000000000000000000000000000000000000000a"
            },
            "toToken": {
              "tokenType": "0x357b0b74bc833e95a115ad22604854d6b0fca151cecd94111770e5d6ffc9dc2b"
            },
            "dexName": "Hyperion",
            "poolId": "0x18269b1090d668fbbc01902fa6a5ac6e75565d61860ddae636ac89741c883cbc",
            "a2b": true,
            "sqrtPriceLimit": "4295048016",
            "poolType": "none",
            "amountIn": "100000000",
            "amountOut": "3249664"
          },
          ...
        ]
      },
      ...
    ]
  }
}
*/


// 2. Build transaction and submit
import { BuildScriptComposerTransaction } from '@aptos-labs/script-composer-sdk';
import { AptosConfig } from '@aptos-labs/ts-sdk';

const transaction = await BuildScriptComposerTransaction({
  sender: address,
  aptosConfig: new AptosConfig({
     network: Network.MAINNET,
  }),
  builder: async (builder) => {
    await HyperionSDK.Swap.generateAggregateSwapTransactionScript({
      ...aggregatorRoutes,
      builder,
      // custom setting. 
      // Default is 'hyperion-aggregator', if don't set.
      partnershipId?: 'your-platfrom-name/co-activity-name' 
    });

    return builder;
  },
});

// extract the payload
const {
  rawTransaction: { payload },
} = transaction as any;

// submit the transaction
const { hash } = await walletCore?.signAndSubmitTransaction({
  data: {
    bytecode: payload.script.bytecode,
    functionArguments: payload.script.args,
    typeArguments: payload.script.type_args,
  },
});
```



{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
