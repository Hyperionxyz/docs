# Add liquidity

## Function

For adding liquidity into position , use `add_liquidity` in `pool_v3` module.

```
 public fun add_liquidity(
        user: &signer,
        position: Object<position_v3::Info>,
        liquidity_delta: u128,
        fa_a: FungibleAsset,
        fa_b: FungibleAsset
    ):(u64, u64, FungibleAsset, FungibleAsset) {
       ...
    }
```

`liquidity_delta`: liquidity amount desired to added into position

`fa_a`: token a fungible asset

`fa_b`: token b fungible asset
