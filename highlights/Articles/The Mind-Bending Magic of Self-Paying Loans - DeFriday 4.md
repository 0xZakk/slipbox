# The Mind-Bending Magic of Self-Paying Loans - DeFriday #4

## Meta Data

Source:  https://every.to/almanack/alchemix-self-paying-loans 
Author: every.to

- Imagine a world where loans don’t have interest.
  One where instead of having assets that are appreciating, and debt that’s also growing, the appreciation on your assets is automatically paying down your debt.
- Enter Alchemix: a new kind of DeFi protocol that allows anyone to borrow against the future yield of their assets.
- In other words, self-repaying loans.
- A platform where you can deposit crypto assets, borrow against them, and then have the future yield on those assets automatically pay off your debt. A loan whose value only goes down, and where your collateral can never get liquidated.
- ## What is Alchemix?
- Alchemix is a fundamentally new financial tool. It blends aspects of a savings account with aspects of a lender, allowing you to earn interest on your deposits as well as borrow against them. Your earned interest automatically pays down your loan amount, meaning your loan never increases, and since you’re borrowing the same asset you’re using as collateral, you can never get liquidated.
- To use it, you first need to deposit funds into Alchemix in the form of DAI, one of the most popular stablecoins pegged to the US Dollar on Ethereum. That DAI goes into the “Vault,” and immediately starts earning interest.
- As soon as your funds are deposited, you can immediately borrow up to 50% of the value of those deposits as “alUSD,” another stablecoin pegged to the US Dollar that’s created by Alchemix.
- Then you can take that alUSD and do whatever you want with it. You could cash it back out to fiat dollars, you could buy Bitcoin or Ethereum, it’s all yours.
- So now you have X dollars deposited in Alchemix, and X/2 dollars borrowed from Alchemix. What makes Alchemix special is your loan amount does not go up. It only goes down. Because instead of the interest on your deposits going on top of your deposits, it goes directly to paying down your debt.
- Alchemix is taking advantage of the larger base return on your assets in order to pay down your smaller liabilities. It’s similar to how reducing costs is often a better way to increase a business’s net margin than increasing revenue. You’ve doubled your effective interest rate by putting your earned interest straight towards paying down your debt.
- The whole thing gets even crazier when you consider that TradFi interest rates on assets are basically 0 (or, say, 7% if you want average S&P returns), but Alchemix historically offers 10-20% interest on DAI.
- ## The Alchemix Mortgage
- Say you’re buying a $300,000 house as your primary residence. You qualify for the best Fannie & Freddie loans at 2.5% interest and 3.5% down, so you only need to put down $10,500. You actually have $25,000 in cash though, and you debate putting all of it down, but instead you put it all in Alchemix first.
- You borrow $12,500 from Alchemix and supply that as a down payment. Now you’ve covered the down payment, but you still have that $25,000 in Alchemix earning interest you can borrow against. Every month you’ll be able to borrow another $208 from your debt being automatically repaid, which you could put towards paying the monthly mortgage cost.
- Or, assuming the mortgage on that house would cost $1,685 per month (that’s what Nerdwallet tells me for Nashville as an example), if you got up to $202,200 in Alchemix the earned interest would completely cover your mortgage.
- ## Alchemix Financial Independence
- You go deep down the Mr. Money Mustache rabbithole and decide you want to pursue “FIRE” Financial Independence, Retire Early.
  You’re making $100,000, so you radically cut your expenses to invest $50,000 a year. After 7 years, you’ve saved $506,000 (with compounding interest), enough to withdraw the $50,000 per year you’re used to living on and have the principal automatically earn back the difference. You can now retire early! Or you keep working and adding more on top, steadily increasing how much of a lifestyle can be passively funded by DeFi.
- ## Alchemix Stacking
- Here’s where things start to get a little strange. Let’s say you’re the Nomad, and you only have $100,000. That’s not enough to live on at $1,500 a month since you can only withdraw $833 a month, right?
- Well… Another option would be to withdraw the max debt, $50,000, and put it back on top of your 100k. Now you have 150k paying down 50k of debt, and you can take out another $25k. So you take that out and put it on top, and now you have 175k. Then you do it one more time, and now you have $187,500 with $87,500 of debt but you’re earning $18,750 a year or $1,562.5 per month.
- The big downside is that if you have a sudden expense come up you no longer have that debt reserve, but your $100k is now earning 37.5% and you can go live off it in Chang Mai. Anything you don’t spend goes towards paying down that debt, and eventually you could have that $187,500 debt free.
- You could do this in the Early Retirement example too. You don’t actually need the whole $500,000 saved up, you can do it with about $260,000. Just stack it a few times, and as long as you don’t need the buffer for an unexpected expense, you’ll have enough to support your lifestyle.
- ## How Alchemix Works
- This all seems a little crazy and too good to be true, so let’s look at the mechanics of Alchemix and try to figure out what’s going on.
- First, how is your debt getting repaid? Well, when you deposit your DAI into Alchemix, they stake it in a DAI Yearn vault like I wrote about in my article on automatic asset allocation.
- The interest rate you earn on Alchemix for DAI is higher than the interest rate for DAI on Yearn though, so where’s the extra interest coming from?
- Well Alchemix gets a slightly better rate because of their volume, but they also have a bonus treasury of DAI in the “Transmuter” which is also earning interest on Yearn, and that interest goes to Alchemix users as a bonus. The Transmuter was originally used to convert alUSD back to DAI, but as Alchemix has gotten more popular the Curve pool for alUSD has gotten more popular and currently has over 250,000,000 alUSD in it, providing so much liquidity for trades that Alchemix users can skip the Transmuter entirely.
- The Transmuter still provides an essential service by making sure alUSD maintains its $1 peg, but it’s able to do so extremely effectively while also earning interest on the approximately 159,000,000 DAI currently stored in it. When the market crashed a few weeks ago, alUSD was one of the most stable stablecoins in the market, providing a great stress test for the Transmuter’s ability to maintain peg while earning interest.
- How does Alchemix get paid? Well they’re getting a slightly better interest rate than they’re paying to you, and they’re collecting some of that difference. 10% of the profit Alchemix earns for its users is stored in the Alchemix treasury, which is used for anything from paying the team to awarding bug bounties. This aligns Alchemix’s incentives nicely with its customers. They only get paid if they make a good return for their users, so they’re incentivized to find the best balance of high return and low risk.
- Compared to other DeFi projects I’ve covered, Alchemix is deceptively simple. You put in DAI, you borrow alUSD, and your debt gets repaid by interest from Yearn. But it’s a great example of how the composability of different applications in DeFi allow for interesting new projects to be created by building on each other. Alchemix is built on Yearn, which is built on Compound, AAVE, and many other apps, which are all built on Ethereum.
- ## Alchemix Risks
- Alchemix’s strength is how it leverages other DeFi protocols to build a new kind of lending protocol where your debt is automatically repaid and you can’t be liquidated.
- The potential weakness is that since it’s built on top of those other DeFi protocols, failures further down the stack could cascade and harm Alchemix through no fault of its own.
- That said, Alchemix has been audited, and they’re also implementing a “continuous auditing” system for their V2 launch later this year. They’re clearly prioritizing security and covering their bases as much as possible, but as always with DeFi, it’s a new and experimental world and anything could happen.
