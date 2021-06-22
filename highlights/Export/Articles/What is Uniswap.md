https://docs.uniswap.org/

What Is Uniswap?
-   Protocol, Interface, Labs   
    -   To begin, we should make clear the distinctions between the different areas of "Uniswap", some of which may confuse new users.
        -   Uniswap Labs: The company which developed the Uniswap protocol, along with the web interface.
        -   The Uniswap Protocol: A suite of persistent, non-upgradable smart contracts that together create an automated market maker, a protocol that facilitates peer-to-peer market making and swapping of ERC-20 tokens on the Ethereum blockchain.
        -   The Uniswap Interface: A web interface that allows for easy interaction with the Uniswap protocol. The interface is only one of many ways one may interact with the Uniswap protocol.
        -   Uniswap Governance: A governance system for governing the Uniswap Protocol, enabled by the UNI token.
    -   The following is a brief overview of the Uniswap protocol
-   Introduction
    -   The Uniswap protocol is a peer-to-contract\[1\] system designed for exchanging cryptocurrencies [(ERC-20 Tokens)](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) on the [Ethereum](https://ethereum.org/) blockchain. The protocol is implemented as a set of persistent, non-upgradable smart contracts; designed to prioritize censorship resistance, security, self-custody, and to function without any trusted intermediaries who may selectively restrict access.
-   How does the Uniswap protocol compare to a typical market?
    -   To understand how the Uniswap protocol differs from traditional exchange, it is helpful to first look at two subjects: how Automated Market Maker design deviates from traditional central limit order book-based exchanges, and how permissionless systems depart from conventional permissioned systems.
    -   Order Book VS AMM
        -   Most publicly accessible markets use a central limit [order book](https://www.investopedia.com/terms/o/order-book.asp) style of exchange, where buyers and sellers create orders organized by price level that are progressively filled as demand shifts.
        -   The Uniswap protocol takes a different approach, using an Automated Market Maker (AMM), sometimes referred to as a Constant Function Market Maker, in place of an order book.
        -   At a very high level, an AMM replaces the buy and sell orders in an order book market with a liquidity pool of two assets, both valued relative to each other. As one asset is traded for the other, the relative price of the two assets shift, and a new market rate for both is determined.
        -   In this dynamic, a buyer or seller trades directly with the pool, rather than with specific orders left by other parties.
    -   Permissionless Systems
        -   The second departure from traditional markets is the permissionless design of the Uniswap protocol. Permissionless design means that the protocol’s services are entirely open for public use, with no ability to selectively restrict who can or cannot use them: anyone can swap, provide liquidity, or create new markets at will.