# via API

Hyperion using Graphql API from Alcove

> Endpoint: [https://hyperfluid-api.alcove.pro/v1/graphql](https://hyperfluid-api.alcove.pro/v1/graphql)



### Get Pool Stat&#x20;

Return stat info about pool / pools (without param `$poolId`)

```
query MyQuery($poolId: String = "") {
  api {
    getPoolStat(poolId: $poolId) {
      dailyVolumeUSD     // 24 hour volume in USD
      farmAPR            // reward APR, %
      feeAPR             // fee APR, %
      feesUSD            // fee in USD
      id                 // pool id
      tvlUSD             // TVL in USD
      pool {
        currentTick      // current tick
        activeLpAmount   // active lp amount
        feeRate          // fee rata, 100 = 0.01% 
        sqrtPrice        // current sqrt price
        token1           // token1 FA address 
        token2           // token2 FA address
      }
    }
  }
}
```
