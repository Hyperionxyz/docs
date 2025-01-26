# Remove Liquidity

When you want to adjust the liquidity of your position or withdraw liquidity from the position, you can use the following method.

## 1. Remove liquidity by inputting liquidity value

use `sdk.Position.removeLiquidityTransactionPayload` method

### Function Input params

* `positionId` : The pool id
* `currencyA`:  coin/fa type of currency token
* `currencyB`:  coin/fa type of currency token
* `currencyAAmount`: the amount about currency A, which used to remove liquidity
* `currencyBAmount`: the amount about currency B, which used to remove liquidity
* `deltaLiquidity` : remove liquidity amount
* `slippage` : slippage value. 0.1 means 0.1%.
* `recipient` : recipient address

### Exmaple

```typescript

const position = await sdk.Position.fetchPositionById({
  positionId: '',
  address: '',
})

/*
[
  {
    "objectId": "0x4b65447d775934596686ef643ad10f3f552b35ff5c2d1bf992c616e4b527fe77",
    "poolId": "0xf1083e26e765506c9360d6b07c1478e6bc40376848b4ee44f4f3c729cf2876b5",
    "txnTimestamp": "2024-12-23T16:36:49.417659+08:00",
    "currentAmount": 396855612,
    "position": {
      "tickLower": 22410,
      "tickUpper": 25930
    },
    "pool": [
      {
        "currentTick": 22971,
        "feeRate": 500,
        "feeTier": 1,
        "poolId": "0xf1083e26e765506c9360d6b07c1478e6bc40376848b4ee44f4f3c729cf2876b5",
        "senderAddress": "0xa5647cdb26df359efb506b5e06a320349b34bbc995314a35f3670a98a210afc6",
        "sqrtPrice": 58172517897304750000,
        "token1": "0x000000000000000000000000000000000000000000000000000000000000000a",
        "token2": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
        "token1Info": {
          "assetType": "0x000000000000000000000000000000000000000000000000000000000000000a",
          "bridge": null,
          "coinMarketcapId": "21794",
          "coinType": "0x1::aptos_coin::AptosCoin",
          "coingeckoId": "",
          "decimals": 8,
          "faType": "0xa",
          "hyperfluidSymbol": "APT",
          "logoUrl": "https://hyperfluid.xyz/aptos-token/main/logos/APT.svg",
          "name": "Aptos Coin",
          "symbol": "APT",
          "isBanned": false,
          "websiteUrl": "https://aptosfoundation.org"
        },
        "token2Info": {
          "assetType": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
          "bridge": null,
          "coinMarketcapId": "",
          "coinType": "0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T",
          "coingeckoId": "",
          "decimals": 6,
          "faType": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115",
          "hyperfluidSymbol": "hfShaq",
          "logoUrl": "",
          "name": "Shaq",
          "symbol": "hfShaq",
          "isBanned": false,
          "websiteUrl": null
        }
      }
    ]
  }
]
*/

const [currencyAAmount, currencyBAmount] = await sdk.Position.fetchTokensAmountByPositionId({
  positionId,
})

const removeRatio = 0.5

const params = {
  positionId,
  currencyA: "0x1::aptos_coin::AptosCoin",
  currencyB:
    "0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T",
  currencyAAmount: parseInt(currencyAAmount * remoteRatio),
  currencyBAmount: parseInt(currencyBAmount * remoteRatio),
  deltaLiquidity: parseInt(position[0].currentAmout * remoteRatio),
  slippage: 0.1,
  recipient: accountAddress,
}

const payload = await sdk.Position.removeLiquidityTransactionPayload(params)
console.log(payload)
```

