# Liquidity Withdrawal Rate Limits

### Overview

Hyperion DEX implements rate limiting and fridge features to protect the platform and user assets. These features are designed to prevent large-scale rapid liquidity withdrawals while ensuring your funds remain safe at all times.

### What is Rate Limiting?

Rate limiting is a protective mechanism that restricts the amount of assets that can be withdrawn from liquidity pools within a specific time period. This helps to:

* Prevent from the market manipulation
* Protect liquidity providers
* Maintain market stability
* Prevent malicious attacks

#### How Rate Limiting Works

The system uses a "token bucket" algorithm, like a bucket that automatically refills:

1. **Initial Capacity**: Each asset has an initial withdrawal limit
2. **Using the Limit**: When you remove liquidity, it consumes the limit
3. **Automatic Refill**: Limits recover automatically over time
4. **Accelerated Recovery**: Adding liquidity immediately restores part of the limit

#### Three Types of Rate Limits

**1. Single-Asset** **Global Rate Limit**&#x20;

* **Scope**: Restricts total withdrawals of specific assets across all platform users
* **Protection Goal**: Prevents rapid depletion of liquidity pools, protects the entire ecosystem
* **Current Limits** (24-hour period):
  * **APT**: 1 million tokens
  * **USDT**: 6 million tokens
  * **USDC**: 5 million tokens
* **Note**: These values are dynamically adjusted based on platform usage. A query page will be available in the future for users to check current thresholds

**2. Single-Asset** **Personal Rate Limit**&#x20;

* **Scope:** Applied to each wallet address
* **Cycle:** 24-hour rolling window
* **Limits:** Each address has a unified 24-hour withdrawal quota, while specific thresholds vary by asset and adjust dynamically based on market conditions
* **Interface Reminder:** When a transaction about to approach the limit, the interface displays a warning message so you can plan withdrawals accordingly

**3. Global USD-Denominated Withdrawal Limit**

* **Scope:** APT, kAPT, amAPT, wBTC, xBTC, aBTC, RION, USDT, USDC and USD1
* **Cycle:** 24-hour rolling window
* **Limits:** All withdrawals of the above assets—converted into their USD-equivalent value—share a unified $10M total 24-hour withdrawal quota across the platform. Specific thresholds adjust dynamically based on market conditions.
* **Note:** A query page will be available in the future for users to check current thresholds.

### What is the Fridge Feature?

When your transaction exceeds rate limits, your funds don't disappear - they're safely stored in the "fridge". This ensures your funds remain secure even when rate limits are triggered.

#### How the Fridge Works

1. **Trigger Condition**: When you try to remove liquidity but exceed rate limits
2. **Automatic Storage**: Your funds are automatically stored in your personal fridge
3. **Freeze Period**: Funds are frozen for 24 hours (default)
4. **Claiming Funds**: After the freeze period, you can claim your funds anytime

### How to Use These Features

#### When Rate Limits are Triggered

If your transaction triggers rate limits:

1. **Don't worry**: Your funds are safe
2. **Check the fridge**: You'll see a new "box" in your fridge
3. **Note the information**:
   * Box ID
   * Amount of tokens frozen
   * Release time (usually 24 hours later)

#### Claiming Funds from the Fridge

**Method 1: Claim All Available Funds**

The simplest way is to claim all unfrozen funds at once:

```
Click the "Claim All Available" button
```

**Method 2: Claim Specific Box**

If you only want to claim specific funds:

```
1. View your fridge box list
2. Find boxes that are unfrozen (showing "Claimable" status)
3. Click the "Claim" button for that box
```

#### Viewing Fridge Status

You can always check:

* **All Fridge Boxes**: Shows detailed information for each box
* **Release Time**: When each box can be claimed
* **Token Information**: Type and amount of frozen tokens
* **Associated Info**: Related pool and position IDs

### Frequently Asked Questions

#### 1. Why was my transaction limited?

Since only global limits are currently active, your transaction was limited because:

* The platform's 24-hour withdrawal volume for the asset is approaching or has reached the threshold
* Your withdrawal amount would cause the global limit to be exceeded
* For example: If APT withdrawals are approaching 1 million tokens in 24 hours, your large withdrawal may be restricted

#### 2. How can I avoid triggering rate limits?

* **Check Status**: Before large operations, check the platform's remaining quota (feature coming soon)
* **Batch Operations**: Split large withdrawals into smaller transactions
* **Avoid Peak Times**: Choose periods with less platform activity
* **Balanced Operations**: Adding liquidity helps restore global limits

#### 3. What privileges do whitelisted users have?

Whitelisted users (like market makers or partners) can:

* Completely bypass rate limits
* No withdrawal restrictions
* No need to use the fridge feature

#### 4. Can the freeze period be shortened?

* Default freeze period is 24 hours
* Regular users cannot change freeze time
* In emergencies, administrators can assist

#### 5. Are my funds safe in the fridge?

Yes, absolutely safe:

* Funds are stored in smart contracts
* Only you can claim after unfreezing
* All operations are logged with events
* Administrators can only intervene in emergencies

#### 6. Do global limits affect all operations?

No, global limits only affect liquidity removal operations:

* **Not affected**: Trading (Swap), adding liquidity
* **Affected**: Removing liquidity, closing positions
* This design protects liquidity pools while maintaining normal trading

#### 7. How can I check current global limit status?

A dedicated page will be launched in the future showing:

* 24-hour limit thresholds for each asset
* Currently used quota
* Remaining available quota
* Limit recovery countdown

### Best Practices

1. **Spread Operations**: Avoid large one-time withdrawals, especially near threshold limits
2. **Follow Announcements**: Limit thresholds may be adjusted, stay updated with official announcements
3. **Be Patient**: The 24-hour freeze period protects the entire ecosystem
4. **Plan Accordingly**: For large withdrawals, plan ahead and execute in batches

### Summary

Rate limiting and fridge features are important security features of Hyperion DEX. They protect platform stability while ensuring your funds remain safe and accessible. By understanding and properly using these features, you can better manage your liquidity operations while contributing to the healthy development of the entire ecosystem.

Remember: These limits aren't obstacles - they're protections. They ensure long-term market stability and benefit all participants.



{% include ".gitbook/includes/disclaimer-description-on-footer.md" %}
