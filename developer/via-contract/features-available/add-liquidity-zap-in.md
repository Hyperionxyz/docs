# Add liquidity (zap in)

## Function

To add liquidity to a position using a single asset (a "zap in" transaction), use the `add_liquidity_single` function in the `router_v3` module.

This function simplifies liquidity provision by allowing a user to provide only one of the two assets in the pair. The contract will automatically swap a portion of the input asset for the other asset to create a balanced liquidity position.

```rust
public entry fun add_liquidity_single(
    lp: &signer,
    lp_object: Object<position_v3::Info>,
    from_a: Object<Metadata>,
    to_b: Object<Metadata>,
    amount_in: u64,
    slippage_numerators: u256,
    slippage_denominator: u256,
    threshold_numerator: u256,
    threshold_denominator: u256
) {
    // ... function body ...
}
```

### Parameters

| Parameter               | Type                        | Description                                                                                                                                              |
| ----------------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `lp`                    | `&signer`                   | The signer of the transaction, representing the liquidity provider.                                                                                      |
| `lp_object`             | `Object<position_v3::Info>` | The specific liquidity position object to which liquidity will be added.                                                                                 |
| `from_a`                | `Object<Metadata>`          | The metadata of the token you are providing.                                                                                                             |
| `to_b`                  | `Object<Metadata>`          | The metadata of the other token in the liquidity pair.                                                                                                   |
| `amount_in`             | `u64`                       | The total amount of token `from_a` you wish to provide.                                                                                                  |
| `slippage_numerators`   | `u256`                      | The numerator for calculating slippage tolerance on the internal swap. For a 1% slippage, this would be `99`.                                            |
| `slippage_denominator`  | `u256`                      | The denominator for calculating slippage tolerance, typically `100`. Defines the minimum amount of token `to_b` you are willing to accept from the swap. |
| `threshold_numerator`   | `u256`                      | The numerator for the swap ratio threshold. For example, `60`.                                                                                           |
| `threshold_denominator` | `u256`                      | The denominator for the swap ratio threshold, typically `100`. This pair of parameters sets a safety limit on the swap.                                  |

### Detailed Parameter Explanation

#### **Slippage Tolerance (`slippage_numerators` / `slippage_denominator`)**

This controls the price risk during the internal swap.

* **Example**: Setting `slippage_numerators` to `99` and `slippage_denominator` to `100` means you are setting a **1% slippage tolerance**.
* **Meaning**: The transaction will only succeed if the amount of `to_b` received from swapping `from_a` is at least 99% of the expected amount based on the current pool price. This protects you from unfavorable price movements during the transaction.

#### **Swap Ratio Threshold (`threshold_numerator` / `threshold_denominator`)**

This is a critical safety feature to prevent an unbalanced deposit due to poor market prices or low liquidity. It limits the maximum percentage of your input `amount_in` that can be swapped for the other token.

* **Example**: Setting `threshold_numerator` to `60` and `threshold_denominator` to `100` means you allow **at most 60%** of your `amount_in` to be swapped for token `to_b`.
* **Meaning**: If the contract calculates that it needs to swap more than 60% of your input asset to create a balanced position, the transaction will be aborted. This protects you from situations where the pool is heavily imbalanced, which would otherwise cause you to sell a large portion of your input asset at a poor price.
