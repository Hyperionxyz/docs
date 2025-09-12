---
description: >-
  This page illustrates how individual APRs vary based on the proportion of
  active liquidity each provider contributes within the fee-generating price
  bin.
---

# APR Calculation for Liquidity Pools and Positions

### Formula

Pool APR = (Fees+Rewards) / Active Pool Value

Your Position APR = (Fees+Rewards) \* (Your Active Position LP Units / Active Pool LP Units) / Your Position Value

### Example

Consider a pool with three liquidity providers where the current price is in bin P.

* A deposits $1000 entirely within the active price bin P and receives 1000 active LP units.
* B deposits $1000, spreading it evenly across 100 bins, receiving only 9 active LP units.
* C deposits $1000, but none of the funds falls into bin P, so this position is inactive and receives 0 active LP units.
* The pool generated $100 in fees within bin P.

**APR Calculation:**

* Pool APR = $100/$2000 = 5%
* A's Position APR = $100\* (1000 /1009) / $1000 = 9.91%
* B's Position APR = $100\* (9 /1009) / $1000 = 0.089%
* C's Position APR = $100\* (0 /1009) / $1000 = 0%



Understand the APR Calculation from a real-world example:

[https://hyperionxyz.medium.com/understanding-hyperion-lp-apr-through-a-parking-lot-analogy-061c7a1c4e95](https://hyperionxyz.medium.com/understanding-hyperion-lp-apr-through-a-parking-lot-analogy-061c7a1c4e95)
