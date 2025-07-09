# Remove liquidity (zap out)

## Function

To withdraw liquidity from a position and receive the funds as a single asset (a "zap out" transaction), use the `remove_liquidity_single` function in the `router_v3` module.

This function simplifies the withdrawal process. It takes your liquidity position (composed of two assets), removes it from the pool, and automatically swaps one of the assets for the other, so you receive the entire value in a single, specified token.

```rust
public entry fun remove_liquidity_single(
    lp: &signer,
    lp_object: Object<position_v3::Info>,
    liquidity_delta: u128,
    to_meta: Object<Metadata>,
    slippage_numerators: u256,
    slippage_denominator: u256
) {
    // ... function body ...
}
```

### Parameters

| Parameter              | Type                        | Description                                                                                                                                                                                                             |
| ---------------------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `lp`                   | `&signer`                   | The signer of the transaction, representing the liquidity provider who owns the position.                                                                                                                               |
| `lp_object`            | `Object<position_v3::Info>` | The liquidity position object from which you are withdrawing.                                                                                                                                                           |
| `liquidity_delta`      | `u128`                      | The amount of liquidity units to remove. This is **not a token amount** but an abstract `u128` value representing your share in the pool. To withdraw everything, use the full `liquidity` value from your `lp_object`. |
| `to_meta`              | `Object<Metadata>`          | The metadata of the **single token** you wish to receive as output. For example, if your position is APT/USDT, you can specify the USDT metadata here to receive all your funds in USDT.                                |
| `slippage_numerators`  | `u256`                      | The numerator for calculating slippage tolerance on the internal swap required to consolidate your assets. For a 1% slippage, this would be `99`.                                                                       |
| `slippage_denominator` | `u256`                      | The denominator for calculating slippage tolerance, typically `100`. This protects you from unfavorable price changes during the internal swap.                                                                         |

### Detailed Parameter Explanation

#### **Liquidity Delta (`liquidity_delta`)**

This is the most critical parameter to understand correctly.

* **What it is**: `liquidity_delta` represents the "amount of liquidity" you want to remove, which is an abstract unit calculated by the protocol. It is **not** an amount of Token A or Token B.
* **How to get it**: You typically read the current `liquidity` value from your `lp_object` . If you want to withdraw all your funds, you would pass this full value as the `liquidity_delta`. If you only want to withdraw a portion (e.g., 50%), you would pass half of that value.

#### **Slippage Tolerance (`slippage_numerators` / `slippage_denominator`)**

This setting is crucial because the function performs an internal swap.

* **Example**: Imagine your position is in a APT/USDT pool. When you call this function and set `to_meta` to be USDT's metadata, the function does the following:
  1. Removes your proportional share of APT and USDT from the pool.
  2. Internally swaps the APT portion for USDT.
  3. Sends you the total amount of USDT.
* **Meaning**: The slippage tolerance applies to step 2. Setting `slippage_numerators` to `99` and `slippage_denominator` to `100` means you are willing to accept up to 1% negative slippage on the APT-to-USDT swap. If the price impact is worse than that, the transaction will fail, protecting your funds.
