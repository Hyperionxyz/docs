# Get pools

## 1. Get all pools

use `sdk.Pool.fetchAllPools`  method.

### Example

```typescript
async function fetchAllPools() {
    const poolItems = await sdk.pool.fetchAllPools();
    console.log(poolItems)
}
```



## 2. Get pool by poolId

```typescript
async function fetchOnePool() {
    const pool = await sdk.pool.fetchPoolById({
        poolId: '0xf108...876b5'
    })
}

```

