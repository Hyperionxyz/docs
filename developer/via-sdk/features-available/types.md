# Types

## Pools Item

```typescript
interface PoolItem {
  id: string;
  aprUSD: string;
  dailyVolumeUSD: string;
  feesUSD: string;
  tvlUSD: string;
  pool: Pool;
}
```

## Pool

```typescript

interface Pool {
  currentTick: number;
  feeRate: string;
  feeTier: number;
  poolId: string;
  senderAddress: string;
  sqrtPrice: string;
  token1: string;
  token2: string;
  token1Info: TokenInfo;
  token2Info: TokenInfo;
}
```

## TokenInfo

```typescript
interface TokenInfo {
  assetType: string;
  bridge: string | null;
  coinMarketcapId: string;
  coinType: string;
  coingeckoId: string;
  decimals: number;
  faType: string;
  hyperfluidSymbol: string;
  logoUrl: string;
  name: string;
  symbol: string;
  isBanned: boolean;
  websiteUrl: string | null;
}
```

## Fee & Subsidy

```typescript
interface Subsidy {
    claimed: Array<{
        amount: string;
        amountUSD: string;
        token: string;
    }>;
    unclaimed: Array<{
        amount: string;
        amountUSD: string;
        token: string;
    }>;
}

interface Fee {
    claimed: Array<{
        amount: string;
        amountUSD: string;
        token: string;
    }>;
    unclaimed: Array<{
        amount: string;
        amountUSD: string;
        token: string;
    }>;
}
```



{% include "../../../.gitbook/includes/disclaimer-description-on-footer.md" %}
