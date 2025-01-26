# Get positions

## 1. Get all positions by \`ownerAddress\`

use `sdk.Position.fetchAllPositionsByAddress` method

### Function input params

* `address` : The user account address.

### Example

```typescript
async function fetchPositionsByAddress() {
    const positions = await sdk.Position.fetchAllPositionsByAddress({
        address: '0x7fd8...aedc1'
    })
}

/*
result:
[
    {
  "isActive": true,
  "value": "1.6999804583508067796",
  "subsidy": {
    "claimed": [
      {
        "amount": "15769",
        "amountUSD": "0.00012961559826835815",
        "token": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115"
      }
    ],
    "unclaimed": [
      {
        "amount": "7859",
        "amountUSD": "0.00006459819816037965",
        "token": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115"
      }
    ]
  },
  "fees": {
    "claimed": [
      {
        "amount": "0",
        "amountUSD": "0",
        "token": "0x000000000000000000000000000000000000000000000000000000000000000a"
      },
      {
        "amount": "647",
        "amountUSD": "0.00000531811098228345",
        "token": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115"
      }
    ],
    "unclaimed": [
      {
        "amount": "38",
        "amountUSD": "0.0000031079258626",
        "token": "0x000000000000000000000000000000000000000000000000000000000000000a"
      },
      {
        "amount": "0",
        "amountUSD": "0",
        "token": "0xc5bcdea4d8a9f5809c5c945a3ff5698a347afb982c7389a335100e1b0043d115"
      }
    ]
  },
  "position": {
    "objectId": "0x4b65447d775934596686ef643ad10f3f552b35ff5c2d1bf992c616e4b527fe77",
    "poolId": "0xf1083e26e765506c9360d6b07c1478e6bc40376848b4ee44f4f3c729cf2876b5",
    "tickLower": 22410,
    "tickUpper": 25930,
    "createdAt": "2024-12-23T08:36:50.072Z",
    "pool": {
      "currentTick": 22971,
      "feeRate": "500",
      "feeTier": 1,
      "poolId": "0xf1083e26e765506c9360d6b07c1478e6bc40376848b4ee44f4f3c729cf2876b5",
      "senderAddress": "0xa5647cdb26df359efb506b5e06a320349b34bbc995314a35f3670a98a210afc6",
      "sqrtPrice": "58172517897304752052",
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
  }
}
]
*/
```

## 2. Get position by \`positionId\`&#x20;

use `sdk.Position.fetchPositionById` method.

### Function input params&#x20;

* `positionId`: Position's id
* `address` : The user account address.

### Example

```typescript
async function fetchPositionById() {
    const pool = await sdk.Position.fetchPositionById({
        positionId: '',
        address: '',
    })
    console.log(pool);
}
```

## 3. Get fee history of the position

use `sdk.Position.fetchFeeHistory` method

### Function input params&#x20;

* `positionId`: Position's id
* `address` : The user account address.

### Example

```typescript
async function fetchFeeHistory() {
    const feeHistory = await sdk.Position.fetchFeeHistory({
        positionId: '',
        address: '',
    })
    console.log(feeHistory);
}
```



