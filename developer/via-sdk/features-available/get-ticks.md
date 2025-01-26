# Get ticks

## 1. Batch get ticks by pool ID

use `sdk.Pool.fetchTicks` method

### Function input params

* `poolId` : The pool object ID.

### Example

```typescript
async function fetchTicksByPoolId() {
    await ticks = await sdk.Pool.fetchTicks({
        poolId: ''
    })
}
```



