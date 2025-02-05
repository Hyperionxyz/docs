# Open position

## Function

For opening empty position , use `open_position`function in `pool_v3` module.

```
    public fun open_position(
        user: &signer,
        token_a: Object<Metadata>,
        token_b: Object<Metadata>,
        fee_tier: u8,
        tick_lower: u32,
        tick_upper: u32,
    ): Object<position_v3::Info> {
        ...
    }

```

`tick_lower`: the lower bound position's liquidity located at

`tick_upper`: the lower bound position's liquidity located at

