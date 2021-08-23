---
title: "Provide Liquidity on Uniswap V3"
slug: "provide-liquidity-on-uniswap-v3"
author : ""
type: "reference"
---

## Summary:

This page of the Uniswap documentation walks you through how to set up a liquidity pool on Uniswap for a custom pair of tokens. You can do this relatively easily through the Uniswap app. First, you need to select the pair of tokens you want to create a pool for. Second, you have to select a fee tier for the pool (or use the one provided). Then you set a price range for the pool. Fourth,you deposit the initial liquidity in the pool. Finally, you review and approve the pool.

## Highlights:

Provide Liquidity on Uniswap V3: How to provide liquidity on Uniswap V3

-   In Uniswap v3, LP’s can concentrate their capital within custom price ranges, providing greater amounts of liquidity at desired prices.
    
-   Whereas Uniswap v2 required all users to provide liquidity across the entire price curve from 0 to infinity, Uniswap v3 allows Liquidity Providers (LPs) to optionally concentrate capital in the price range they believe will generate the highest return.
    
-   This guide will walk you through the steps to provide liquidity via the Uniswap app.
    
-   How to Provide Liquidity on Uniswap V3
    
-   1. Select Pair
    
-   The first step is to select which pair of tokens you wish to provide as liquidity. Any pair of [ERC-20](https://eips.ethereum.org/EIPS/eip-20) tokens is valid, but each pair has different characteristics.
    
-   You may wish to consider factors such as TVL, trading volume, and your assessment of the risk that these token prices diverge in the future.
    
-   2. Review Fee Tier
    
-   Once you’ve selected a pair of tokens, the next step is to select the right fee tier.
    
-   Every pair of tokens offers three fee tiers:
    
-   0.05% fee tier: Best for stable pairs
    
    -   The 0.05% fee tier is ideal for token pairs that typically trade at a fixed or highly correlated rate, such as stablecoin-stablecoin token pairs (e.g. DAI-USDC). LPs take on minimal price risk in these pools, and traders expect to pay minimal fees.
        
-   0.3% fee tier: Best for most pairs
    
    -   The 0.30% fee tier is best suited for less correlated token pairs such as the ETH-DAI token pair, which are subject to significant price movements both to the upside and downside. This higher fee is more likely to compensate LPs for the greater price risk that they take on relative to stablecoin LPs.
        
-   1.0% fee tier: Best for exotic pairs
    
    -   The 1.00% fee tier is designed for exotic assets, where LPs take on extreme price risk (e.g. ETH-GTC). Relevant assets are those that are particularly subject to monotonic price movements.
        
-   The app will auto-select the fee tier with the most liquidity because that is a good heuristic.
    
-   In most cases, LPs will align around one fee tier for a pair.
    
-   If you’re new to LP’ing, we recommend using the auto-selected fee tier. However, advanced LP strategies may find it worthwhile to provide liquidity in the other fee tiers.
    
-   3. Set Price Range
    
-   Next you need to choose a price range in which to provide liquidity. When making a price range decision, you should consider the degree to which you think prices will move over the course of your position's lifetime.
    
-   You should also consider your willingness to actively manage the position as the market evolves, and the economics of transactions required to actively manage a position.
    
-   If the price moves outside your specified range, then your position will be concentrated in one of the two assets and not earn trading fees until the price returns to their range.
    
-   Note that your price will snap to the nearest tick. Don't worry if you're unable to type in a nice round number! This is [expected](https://help.uniswap.org/en/articles/5455578-why-does-the-price-input-automatically-round-to-a-seemingly-random-number) because of how ticks work in Uniswap v3.
    
-   nstead of picking a price range, you can provide liquidity across the Full Range like in Uniswap v2 by clicking the Full Range button. However, please note your rate of return will be significantly lower than a similar position with a more narrow price range.
    
-   The following community tools simulate Uniswap v3 positions and help you evaluate your price range.
    
    -   [Flipside Uniswap V3 calculator](https://uniswapv3.flipsidecrypto.com/)
        
    -   [Defi-lab.xyz](https://defi-lab.xyz/uniswapv3simulator)
        
    -   [Chainvault.io](https://app.chainvault.io/#/tools/ilcalc)
        
-   4. Deposit Amounts
    
-   With your pair, fee tier, and price range selected, you can now decide how much capital to contribute to this position.
    
-   Enter a value in one of the ‘Deposit Amounts' boxes and the other box will automatically populate the corresponding amount. The ratio of these two fields is based on the position of your price range around the market price. If your price range skews more toward one side of the market price, then you will provide more of that asset. This can be okay -- it is not necessary to target a [50/50 ratio](https://help.uniswap.org/en/articles/5455528-why-is-my-lp-deposit-not-50-50-split-between-the-two-tokens) though some strategies may choose that ratio.
    
-   ### 5. Approve and Add
    
-   Finally, you are ready to submit the transaction. First, you may need to approve the Uniswap v3 router contract to spend tokens on your behalf. This is only necessary the first time you provide liquidity with a token.

## Literature Notes

- 

## Meta Data

**Source:** 
**Domain(s):**
- 
