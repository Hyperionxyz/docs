# How to Place a Recurring Order

The **Recurring** function enables users to perform **on-chain Dollar-Cost Averaging (DCA)** by scheduling multiple smaller swaps over time, rather than a single lump-sum trade.

#### **Key Features:**

* **Selling**: Choose the token and amount you want to invest.
* **To Buy**: Select the asset you want to accumulate.
* **Every**: Define the frequency of trades (e.g., every 1 minute, 1 hour, 1 day).
* **Over**: Define the total number of scheduled trades (e.g., 2 orders, 10 orders).
* **Price Range (optional) –** Set a minimum and maximum price band. Trades will only execute if the market price remains within this band.
* **Market Rate**: Shows the current exchange rate for reference.
* **Execution Fee**: Paid only when the order is executed, rewarded to the executor.
* **Gas Fee**: Covers network cost, paid to the executor.
* **Platform Fee**: Charged by the DEX, currently free.

Hyperion is an **open protocol** — anyone can execute Trigger orders and earn the Execution and Gas fees. Users only pay these fees when their orders are successfully executed.

Once the frequency, trade count, and price conditions are set, the system automatically executes the Recurring swaps whenever those conditions are met.

***

### Guide

1. Select Recurring ModeOn the Swap page, select **Recurring** (highlighted in red). This switches the interface from _Instant Swap_ to _Recurring (DCA scheduling)_.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

2. Enter Order Details

* **Selling**: Enter the token and amount you want to invest.
* **To Buy**: Select the token you want to accumulate.
* **Every**: Choose the frequency of each swap (e.g., every 1 minute / 1 day / 1 week).
* **Over**: Define the total number of trades (e.g., 2 orders, 10 orders).
* **Price Range (optional)**: Set a minimum and maximum price — trades only execute within this band.

⚠️ **Important:** The _Every_ + _Over_ fields determine how your total investment is split over time.

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

3. Create Order

* Review the **Recurring Summary** before confirming:
  * **Sell Total** (e.g., 100 USDT)
  * **Sell per Order** (e.g., 50 USDT)
  * **To Buy** (expected APT)
  * **Order Interval** (e.g., 1 minute)
  * **Estimated Expiry** (based on frequency × number of orders)
  * **Fees** (Platform Fee = 0, Gas Fee covered)
* Click **Create Order** (red box) to finalize.

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

4. Track Recurring Orders

* After confirmation, your Recurring order appears under _Open Orders_ (highlighted in red).
* Each scheduled trade executes automatically until all trades are completed.
* You can cancel individual orders or use **Cancel All** anytime.

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

{% include "../.gitbook/includes/disclaimer-description-on-footer.md" %}
