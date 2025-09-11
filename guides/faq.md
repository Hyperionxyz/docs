---
description: >-
  As an alternative to the 'APR Calculation for Liquidity Pools and Positions'
  section, this page uses a real-life example to explain Hyperion LP APR
---

# FAQ

### 🅿️ The Complete Parking Lot Analogy

Think of liquidity provision like running a parking lot:

| Concept                 | Parking Lot Analogy           | Hyperion LP Context             |
| ----------------------- | ----------------------------- | ------------------------------- |
| Entire parking lot      | Uniswap V3 Pool               | Pool                            |
| Different parking zones | Different price ranges (bins) | Concentrated liquidity ranges   |
| Parking fees            | Trading fees                  | Swap fees collected by the pool |
| Government subsidies    | Liquidity mining rewards      | Extra rewards for LPs           |
| Parking lot owners      | Liquidity Providers (LPs)     | Users providing liquidity       |
| Drivers                 | Traders                       | Traders using the pool          |
| Open hours              | Price within your range       | Active LP amount                |

🅿️ **Zone A (Downtown)** = Current price range → High traffic, high fees\
🅿️ **Zone B (Suburbs)** = Far from current price → Low traffic, almost no income\
🅿️ **Zone C (Airport)** = Special zone → Occasionally full, but mostly empty



**Key Idea:** Your earnings depend on:

1. Which zone you choose (location)
2. How concentrated your funds are (narrow vs wide range)
3. How many other LPs share the zone (competition)
4. Timing (when you are active in the zone)
5. Subsidies or rewards (boosted income)

***

### ❓ Frequently Asked Questions

#### 1. Why does Pool APR show 30%, but I only earned $1 on $1000 in one day?

**Explanation:**

* Pool APR is an **average across all zones and past periods**.
* Your earnings (Position APR) depend on **your active LP amount** in the fee-generating zone during your active hours.

**Example:**

* Pool collected $1000 fees yesterday:
  * Zone A (downtown) active LP = $50,000 → fees = $900
  * Zone B (suburbs) active LP = $10,000 → fees = $100
* Pool APR = ($1000 / $60,000) × 365 ≈ 608% annualized (just illustrative)
* You deposited $1000 in Zone B → share = $1000 / $10,000 = 10%
* Your earnings = 10% × $100 = $10/day

**Parking lot analogy:**

* Zone A (downtown) = busy lot, collects lots of fees
* Zone B (suburbs) = quiet lot, few cars → even if you open your lot all day, you earn little
* Pool APR averages all zones → looks high, but your lot in Zone B earns very little

***

#### 2. Why do different LPs earn very different amounts with the same deposit?

**Explanation:** Depends on **zone, range width, and competition**.

**Example:**

* LP1 deposits $1000 narrowly in Zone A (active LP = $1000, total pool LP = $1000)
  * Share = 100% → earns $100 in fees
* LP2 deposits $1000 spread across 10 zones, including Zone A (active LP = $100, total pool LP = $1000)
  * Share = 10% → earns $10 in fees
* LP3 deposits $1000 narrowly in Zone B (active LP = $1000, total pool LP = $50,000)
  * Share = 2% → earns $2 in fees

**Parking lot analogy:**

* LP1 runs a single busy lot downtown → collects all parking fees
* LP2 spreads money across multiple lots → most funds idle → collects only a fraction of fees
* LP3 opens a lot in the suburbs with many other owners → even though lot is open, fee share is tiny

***

#### 3. Why did my rewards drop even though the price stayed in my range?

**Explanation:** Could be **competition or wide range**.

**Example:**

* Zone A fees yesterday = $500, active LP = $50,000
* Your active LP = $1000 → share = 2% → earns $10
* Yesterday only you → would have earned $500 → share dropped due to new LPs

**Parking lot analogy:**

* You’re running your lot downtown (Zone A) alone → $500 revenue
* 10 new parking lots open in same area → your share diluted → you only collect $10

***

#### 4. Why did I provide liquidity for one full day but earn almost nothing?

**Explanation:** Multiple factors:

1. Price mostly outside your range → inactive LP
2. Your range too wide → diluted active LP
3. High competition → share of fees is low
4. Joined during low-fee period → Pool APR uses historical average

**Example:**

* LP deposits $1000 across Zones A+B (wide range)
* Active LP yesterday: Zone A = $50,000, Zone B = $20,000
* Fees: Zone A = $500, Zone B = $50
* LP’s effective active LP:
  * Zone A: $1000 / $50,000 = 2% → $500 × 2% = $10
  * Zone B: $1000 / $20,000 = 5% → $50 × 5% = $2.5
* Price in range only 2.5h in Zone A + 1h in Zone B → scale earnings proportionally → total ≈ $1

**Parking lot analogy:**

* You open wide lots in multiple zones
* Cars mostly in Zone A for only a few hours → most of your funds idle
* Even though “active full day,” earnings almost nothing

***

#### 🔑 Key Takeaways

* **Pool APR** = average across all zones, LPs, and time periods
* **Position APR** = your actual share based on range, concentration, timing, and competition
* Factors affecting Position APR:
  1. Zone choice (location)
  2. Range width (concentration of funds)
  3. Competition (other LPs in same zone)
  4. Timing (when price is in your range)
  5. Subsidies or rewards
  6. Active time (price within your range)























{% include "../.gitbook/includes/disclaimer-description-on-footer.md" %}
