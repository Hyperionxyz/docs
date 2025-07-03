# Create pool

For general pool creation, use the `create_pool` function in the `pool_v3` module.

```
    public fun create_pool(
        token_a: Object<Metadata>,
        token_b: Object<Metadata>,
        fee_tier: u8,
        tick: u32,
    ): Object<LiquidityPoolV3> {
        ...
    }
```

## Function params

* `token_a`: The token A object to add liquidity
* `token_b`: The token B object to add liquidity
* `fee_tier`: fee\_iter will affect price precision, they correspond to different fee rates.
* `tick`: initiailize price for pool



{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
