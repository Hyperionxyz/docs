# Concentrated Liquidity

## **Introduction** <a href="#introduction" id="introduction"></a>

The core innovation of Hyperion is allowing concentrated liquidity, whereby users may add their liquidity within custom price ranges. In AMM protocols, which are adopted by most of common decentralized exchanges nowadays, liquidity is distributed uniformly along the entire price curve (0, ∞).

The previous AMM liquidity distribution makes trading available across the full price interval between 0 and infinite upon simple deployment. However, in AMM pools, a significant portion of the liquidity was never utilized by actual transactions, which is a waste of provided liquidity to some extent.

For example, the trading price is usually constant in a stablecoin pair. The liquidity outside its regular price range is rarely touched. In most of mainstream stablecoin trading pools (AMM-based), only less than 1% of their total liquidity are actually being used. The rest of the available liquidity stays idle in the pools all the time.

It’s reasonable for an LP to expect that their liquidity provided can be utilized as much as possible so that they can earn more fees from it. This can be realized with the help of concentrated liquidity. Liquidity providers are able to concentrate their liquidity to their specified price ranges according to the most active price intervals of a particular trading pair. For instance, an LP can choose to add all of their liquidity into the price range (0.995, 1.005) of a stablecoin trading pool. As transactions are happening most actively around the mid-price, these LPs can maximize their liquidity efficiency in this way and earn greater fees from participation.

The liquidity concentration changes the price interval of a user’s liquidity from infinite to finite. For the liquidity that is concentrated to a finite price interval, we can it a position, or a liquidity position. An LP can create multiple positions in a same pool. By setting different price ranges, LPs can simulate different price curves to achieve their custom strategies.

## **Active Liquidity** <a href="#active-liquidity" id="active-liquidity"></a>

Given that a user may set a finite price range for a position, when the asset price goes up and down in a fluctuating market period, the price may exit the price range that is set for the position. In that case, the liquidity in that particular position will not be active and will stop earning fees until the price re-enters the position price range.

If the price of a trading pair increases or decreases in one direction, liquidity providers will gain more of the one token in their positions because it shows more demand for the other token from the swappers. When the price reaches the upper or lower bound of their positions, their entire liquidity will consist of only one asset.

When the price re-enters the range, the liquidity within the position will be active and start earning fees again. The liquidity composition for an active position will be two tokens instead of only one asset type.

LPs have a very high flexibility in concentrated liquidity. They can open as many liquidity positions with their custom price bands as they want and need. The underlying algorithm of concentrated liquidity sets out the mechanism that gives the decision right of the liquidity distribution to the actual market, because most liquidity providers will naturally concentrate their liquidity within the most active price ranges according to the market trends in order to earn more transaction fees.

## **Price Ticks** <a href="#price-ticks" id="price-ticks"></a>

In an AMM model, the price is continuous, while it is sort of different in a concentrated liquidity protocol. The prices in concentrated liquidity positions are discrete. The price curve of concentrated liquidity is partitioned by a number of ticks. A discrete space can be found between each tick and the tick next to it. When we move up and down by one tick, it will show a 0.01% increase or decrease (1 basis point) in price at any point in price space.

We use ticks as borders for every liquidity position. When a liquidity position is opened, it comes with an upper and a lower price tick that are set by liquidity providers.

As the price keeps changing as new swaps are executed, the smart contract tends to consume all the liquidity available in the current tick interval until the next price tick is reached, continually exchanging the outbound asset for the inbound. When a new price tick is reached, the pool contract will immediately switch to the new tick and any dormant liquidity within the newly active tick intervals will be activated.

Although each trading pool has the same number of price ticks in a concentrated liquidity protocol, there are only a part of them serving as active ticks in actual scenarios. There is certain correlation between tick spacing and swap fee tier in a concentrated liquidity smart contract. The lower the fee tier is set, the closer the two nearby active ticks can be. In other words, a higher fee tier can give the pool a wider tick space of potential active price ticks.

For trading pairs that require higher price granularity, like stablecoin pairs, a relatively narrower tick space will be helpful. The price impact during swapping will be more moderate, with the tighter tick spacing, which is exactly what is needed by a stablecoin pool.



{% include "../.gitbook/includes/disclaimer-description-on-footer.md" %}
