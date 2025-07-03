# Data structure

## Pool

```
    #[resource_group_member(group = aptos_framework::object::ObjectGroup)]
    struct LiquidityPoolV3 has key {
        token_a_liquidity: Object<FungibleStore>,
        token_b_liquidity: Object<FungibleStore>,
        token_a_fee: Object<FungibleStore>,
        token_b_fee: Object<FungibleStore>,
        // the current price
        sqrt_price: u128,
        // liquidity current tick
        liquidity: u128,
        // the current tick
        tick: I32,
        // the most-recently updated index of the observations array
        observation_index: u64,
        // the current maximum number of observations that are being stored
        observation_cardinality: u64,
        // the next maximum number of observations to store, triggered in observations.write
        observation_cardinality_next: u64,
        /// The numerator of fee rate, the denominator is 1_000_000.
        fee_rate: u64,
        // the current protocol fee as a percentage of the swap fee taken on withdrawal
        // the denominator is 1_000_000.
        fee_protocol: u64,
        // whether the pool is locked
        unlocked: bool,
        fee_growth_global_a: u128,
        fee_growth_global_b: u128,
        seconds_per_liquidity_oracle: u128,
        seconds_per_liquidity_incentive: u128,
        position_blacklist: PositionBlackList,
        last_update_timestamp: u64,
        tick_info: SmartTable<I32, TickInfo>,
        tick_map: BitMap,
        tick_spacing: u32,
        protocol_fees: ProtocolFees,
        lp_token_refs: LPTokenRefs,
        max_liquidity_per_tick: u128,
        rewarder_manager: RewarderManager
    }

```



## Position

```
    #[resource_group_member(group = aptos_framework::object::ObjectGroup)]
    struct Info has key {
        // whether inited after migration
        initialized: bool,
        // the amount of liquidity owned by this position
        liquidity: u128,
        tick_lower: I32,
        tick_upper: I32,
        // fee growth per unit of liquidity as of the last update to liquidity or fees owed
        fee_growth_inside_a_last: u128,
        fee_growth_inside_b_last: u128,
        // the fees owed to the position owner in token0/token1
        fee_owed_a: u64,
        fee_owed_b: u64,
        token_a: Object<Metadata>,
        token_b: Object<Metadata>,
        fee_tier: u8,
        rewards: vector<PositionReward>,
    }

```



## Rewarder

```
 struct RewarderManager has store {
        rewarders: vector<Rewarder>,
        last_updated_time: u64,
        pause: bool
    }

    struct Rewarder has copy, drop, store {
        reward_store: Object<FungibleStore>,
        emissions_per_second: u64,
        emissions_per_second_max: u64,
        emissions_per_liquidity_start: u128,
        emissions_per_liquidity_latest: u128,
        user_owed: u64,
        pause: bool
    }

    /// The Position's rewarder record
    struct PositionReward has drop, copy, store {
        emissions_per_liquidity_inside: u128,
        amount_owned: u64,
    }

```





{% include "../../.gitbook/includes/disclaimer-description-on-footer.md" %}
