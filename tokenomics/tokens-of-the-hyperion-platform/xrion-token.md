# xRION Token

**Basic Information**

* **Name**: Hyperion Escrowed Token
* **Ticker**: xRION
* **Chain**: Aptos
* **Collection Address**: TBD



### Overview

xRION is the escrowed, non-transferable governance token of the Hyperion platform. xRION can be obtained by converting RION. xRION enables holders to participate in governance within the Hyperion DAO framework (when the DAO is established), as well as to access certain platform features, such as launchpool participation. Further details on conversion mechanisms are provided below.



### Locking RION → Receiving xRION

* Users **lock RION tokens** for a duration between **1 and 52 weeks**.
* For each locked RION, the user receives: **xRION = Locked Amount × Lock Duration (in weeks)**
  * Example: locking 100 RION for 10 weeks yields **1,000 xRION**.



### Epoch Structure

* Time is divided into **weekly Epochs**.
* Each Epoch runs from **Monday 08:00 UTC → next Monday 08:00 UTC**.
* When a user locks RION, their xRION becomes **active from the nearest upcoming Monday Epoch**. The user’s xRION balance is created and visible. The xRION is counted in the reward pool and begins participating in the weekly distribution.



### Reward Distribution

* Once active, xRION allows the user to participate in **weekly reward distributions**.
* Rewards are claimable **at the end of each Epoch**.
* The **first claim** happens when the initial Epoch (after locking) ends.



### Decay of xRION

* xRION has a **linear weekly decay**:
  * Each week, **xRION decreases by 1 per locked RION**.
  * This continues until the lock period ends.
* After the final week, the user’s RION unlocks and can be withdrawn.



### Extending the Lock

* Users can **extend the lock duration at any time before expiry**.
* By extending, the xRION decay schedule is **recalculated** from the new end date, ensuring continued participation in rewards.



### Example Walkthrough

* Alice locks **100 RION** for **4 weeks**.
* At lock time, her allocation is: **xRION = 100 × 4 = 400 xRION**.
* Since the lock is made on **Wednesday**, her xRION becomes active starting the next **Monday 08:00 UTC**.

**Epoch Rewards & Decay:**

* **Week 0:** Alice has locked 100 RION but "my APR" and "xRION" amount will still be 0 on UI
* **Week 1:** Alice will see "400 xRION" and "my APR" and participate fully in reward distribution.
* **Week 2:** Her balance decays to 300 xRION.
* **Week 3:** Balance is 200 xRION.
* **Week 4:** Balance is 100 xRION. At the end of this Epoch, her lock period ends, and she can withdraw 100 RION.

If Alice chooses to extend her lock by another 8 weeks during Week 2, her xRION will be recalculated based on the new lock period, giving her higher weight in upcoming reward distributions.



### Utilities

* **Staking**:\
  By staking RION, users automatically participate and hold xRION and become eligible for xRION staking rewards. These rewards are supported by the treasury of the Hyperion platform and made available on a discretionary basis – further details on the reward program and updates thereto will be published from time to time via official channels. They are a way to give back to the community, sharing the benefits of the growth of the platform.\

* **Governance**:\
  Following the formal establishment of the Hyperion DAO, xRION will enable holders to participate in platform proposals and voting within the DAO. Voting rights will be based on the amount of xRION held, in accordance with the governance framework defined by the DAO (when the DAO is established).\

* **Launchpad Participation**:\
  xRION balances may be used as a whitelist requirement or for calculating allocation quotas for launchpool participation on the Hyperion launchpad.

Further utilities for xRION may be introduced as the Hyperion platform evolves.



### Disclaimer

xRION does not represent any shareholding, ownership, participation, right, title, or interest in Hyperion,their affiliates, or any other company, enterprise, or undertaking. xRION does not entitle token holders to any promise of fees, dividends, revenue, profits, or investment returns, and is not intended to constitute securities in any jurisdiction, including the United States, British Virgin Islands, Hong Kong, Panama, or Singapore. xRION may only be utilized within the Hyperion platform, and ownership confers no rights, express or implied, other than the right to use xRION to interact with and utilize the Hyperion platform. The secondary market price of xRION is not dependent on the efforts of the Hyperion Project contributors, and there are no mechanisms or schemes in place to control or manipulate secondary market pricing. xRION holders are not entitled to vote on the operation or management of Hyperion, their affiliates or their assets, nor does xRION constitute any equity interest or collective investment scheme. The arrangement is not intended to be any form of joint venture or partnership. All governance features described herein are subject to the formal establishment of the Hyperion DAO.



{% include "../../.gitbook/includes/disclaimer-description-on-footer.md" %}
