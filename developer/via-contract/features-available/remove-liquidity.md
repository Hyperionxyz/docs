# Remove liquidity

## Function

For removing liquidity into position , use remove`_liquidity` in `pool_v3` module.

```
 public fun remove_liquidity(
        user: &signer,
        position: Object<position_v3::Info>,
        liquidity_delta: u128
    ): (Option<FungibleAsset>, Option<FungibleAsset>) {
```

`liquidity_delta`: liquidity amount desired to remove out position





{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
