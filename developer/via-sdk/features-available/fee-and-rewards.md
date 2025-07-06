# Fee & Rewards

When you add liquidity within a valid price range, all transaction fees generated within this range will be distributed based on the proportional share of effective liquidity from all positions within the current range. If you intend to harvest transaction fees separately, please follow the method below.

## 1. Fetch Pending Fee Info

You can get all pending/claimed fee info from method `sdk.Position.fetchPositionById` .



## 2. Generate all rewards claim payload

use `sdk.Position.claimAllRewardsTransactionPayload` method

### Function Input Params

* `positionId` : The pool's id
* `recipient` : who will get this fee reward.

### Example

```typescript
const payload = sdk.Position.claimAllRewardsTransactionPayload({
    positionId: '',
    recipient: ''
})
```



## 3. Generate fee claim payload

use `sdk.Position.claimFeeTransactionPayload` method

### Function Input Params

* `positionId` : The pool's id
* `recipient` : who will get this fee reward.

### Example

```typescript
const payload = sdk.Position.claimFeeTransactionPayload({
    positionId: '',
    recipient: ''
})
```



## 4. Generate reward claim payload

use `sdk.Position.claimRewardTransactionPayload` method

### Function Input Params

* `positionId` : The pool's id
* `recipient` : who will get this fee reward.

### Example

```typescript
const payload = sdk.Position.claimRewardTransactionPayload({
    positionId: '',
    recipient: ''
})
```





{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
