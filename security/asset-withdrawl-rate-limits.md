# Liquidity Withdrawal Rate Limits

### Overview

Hyperion DEX implements withdrawal rate limits and the Fridge mechanism as a core security measure to protect user assets and platform liquidity.

These mechanisms are primarily designed to mitigate the risk of hacker attacks or other malicious behaviors that could lead to abnormal, large-scale, rapid liquidity withdrawals, which may otherwise threaten the stability of liquidity pools.

By introducing controlled withdrawal limits and a safety buffer mechanism, Hyperion ensures that user funds remain secure, recoverable, and protected, even under extreme or adversarial conditions.

### What is Rate Limiting?

Rate limiting is a protective mechanism that restricts the amount of assets that can be withdrawn from liquidity pools within a specific time period. This helps to:

* Prevent from the market manipulation
* Protect liquidity providers
* Maintain market stability
* Prevent malicious attacks

#### How Rate Limiting Works

Hyperion uses a USD-denominated quota system.

All limited assets are converted into their USD-equivalent value at the time of withdrawal, and the withdrawal amount consumes a USD-based quota

Key characteristics:

1. **USD-Based Accounting**\
   Withdrawals are measured in USD value, not by individual token amounts
2. **Shared Asset Scope**\
   Supported assets, including APT, goAPT, kAPT, amAPT, wBTC, xBTC, aBTC, RION, USDT, USDC sUSDe and USD1, all draw from the same USD-denominated limits
3. **Rolling Window**\
   Limits are calculated over a rolling 24-hour window
4. **Automatic and Manual Recovery**\
   Withdrawal quotas recover gradually over time as the rolling window advances or, the quotas restore a portion immediately by users adding liquidity (depositing LP).

#### Types of Withdrawal Rate Limits

**1. Global USD-Denominated Withdrawal Limit**

* **Scope**:\
  APT, goAPT, kAPT, amAPT, wBTC, xBTC, aBTC, RION, USDT, USDC, sUSDe, USD1
* **Cycle**:\
  24-hour rolling window
* **Limit**:\
  All withdrawals of the above assets—converted to USD—share a **unified platform-wide withdrawal quota**.
* **Effect**:\
  When the global USD-denominated withdrawal limit is reached:
  * Liquidity removal and position-closing operations from **all users** are affected
  * Withdrawn funds are routed into the **Fridge** instead of being immediately received
* **Note**:\
  The Threshold, currently $5 million USD, is dynamically adjusted based on platform conditions.\
  A public query page will be introduced in the future.

**2. Personal USD-Denominated Withdrawal Limit**&#x20;

* **Scope**:\
  APT, goAPT, kAPT, amAPT, wBTC, xBTC, aBTC, RION, USDT, USDC, sUSEe, USD1
* **Cycle**:\
  24-hour rolling window
* **Limit**:
  * $50,000 USD by default
  * $500,000 USD after activating Hyperauth
* **Effect**:\
  When a personal USD-denominated withdrawal limit is reached:
  * The user must wait for the personal quota to recover, or deposit LP to restore the quota
  * If user insist on withdrawing the funds, withdrawn funds are routed into the **Fridge** instead of being immediately received
* **Interface Reminder**:\
  The interface displays a warning when a withdrawal approaches the personal limit.

### What is the Fridge?

The Fridge is a safety mechanism that temporarily stores withdrawn funds when the global USD-denominated withdrawal limit has been reached.

It ensures that funds remain secure and fully claimable once limits recover.

#### How the Fridge Works

1. **Trigger Condition**\
   The Fridge is triggered when the withdrawal limit is reached
2. **Automatic Storage**\
   Affected withdrawal amounts are automatically placed into the Fridge
3. **Freeze Period**\
   Funds are frozen for 24 hours by default.
4. **Claiming Funds**\
   After the freeze period ends, funds can be claimed at any time

> Personal USD-denominated withdrawal limits do not trigger the Fridge.

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

#### 1. Why was my withdrawal frozen?

Your withdrawal was frozen because it exceeded your Personal Liquidity Withdrawal Limit.

When this limit is reached, a temporary withdrawal freeze is automatically triggered as a security measure.

Please wait 24 hours. After the cooldown period ends, your funds will be automatically unlocked and credited back to your account. No further action is required from your side.

#### 2. How can I avoid being frozen?

* **Balance Operations**: Adding liquidity helps restore personal limits
* **Activate Hyperauth:** After activating Hyperauth, your wallet address will get a far larger personal withdrawal limit of $500,000 USD

#### 3. Can the freeze period be shortened?

* Default freeze period is 24 hours
* In emergencies, please open a ticket and tag admins in Hyperion [Discord](https://discord.com/invite/MYex8tHXtN)

#### 4. Are my funds safe in the fridge?

Yes, absolutely safe:

* Funds are stored in smart contracts
* Only you can claim after unfreezing
* All operations are logged with events
* Administrators can only intervene in emergencies

#### 5. Do withdrawal limits affect all operations?

No, withdrawal limits only affect liquidity removal operations:

* **Not affected**: Trading (Swap), adding liquidity
* **Affected**: Removing liquidity, closing positions



{% include "../.gitbook/includes/disclaimer-description-on-footer.md" %}
