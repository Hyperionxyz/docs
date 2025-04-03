# Get pools

## 1. Get all pools

use `sdk.Pool.fetchAllPools`  method.

### Example

```typescript
async function fetchAllPools() {
    const poolItems = await sdk.Pool.fetchAllPools();
    console.log(poolItems)
}
```



## 2. Get pool by poolId

```typescript
async function fetchOnePool() {
    const pool = await sdk.Pool.fetchPoolById({
        poolId: '0xf108...876b5'
    })
}

```



## 3. Get pool by token asset types and feeTier

(from v0.0.7)

```javascript
async function fetchOnePool() {
    const pool = await sdk.Pool.getPoolByTokenPairAndFeeTier({
        token1: '0x1::aptos_coin::AptosCoin',
        token2: '0x6926bff1eab5554fa72ae167ed736acf623ab17fe81ebf2ea0d2138f8c533f77::type::T',
        feeTier: FeeTierIndex["PER_0.01_SPACING_1"],
    })
}
```

