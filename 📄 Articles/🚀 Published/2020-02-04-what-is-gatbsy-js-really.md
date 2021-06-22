---
title: What is Gatbsy.js, Really?
slug: what-is-gatbsy-js-really
date_published: 2020-02-04T15:00:00.000Z
date_updated: 2021-02-22T17:18:41.000Z
tags: Programming, JavaScript
excerpt: Gatsby.js is often described as a static site generator, but it's really so much more than that.
---

[Gatsby.js](https://www.gatsbyjs.org/) used to be described as a static site generator, built with React and Webpack. The documentation has since shied away from that description and instead now describes Gatsby as a framework that "helps developers build blazing fast websites and apps."

Calling Gatsby a framework is a lot more accurate, given that you can build more than simple static sites with it. But it's still a little short of a full and accurate description.

## Static v Dynamic Sites?

In the days before Gatsby, we could really only categorize a site as either static or dynamic. I used to work at design and development agencies, and we'd ask clients how much they wanted to update the content of their website. We were trying to figure out if we had to build a dynamic site, or if we could get away with building a cheaper and easier static site.

What's the difference?

A dynamic site is one where the HTML for a page is generated *dynamically* on the server; in a static site, the HTML for that page already exists in full.

Dynamic sites are created with tools like WordPress and Drupal and come with a ton of great benefits. The most important of which is that low-tech users can update the content of their site easily without having to dive into the code. The trade-off here are performance. Dynamic sites are slower and can get really sluggish as they get really big.

For a simple content based site, like a blog, a dynamic site is probably overkill, especially for a technical user. At the same time, no one wants to write custom HTML documents by hand. This is exactly what lead to the development of tools like Jekyll and other static site generators. By combining a couple of common tools (like templating) into a single library, we could easily *generate* a static website. You get to host something that is completely static, but you don’t have to build it all.

## How Does Gatsby Fit In?

While Gatsby started its days as a static site generator, but with React instead of a templating language, it has since far outgrown those roots. Gatsby has also outgrown this dichotomy of static versus dynamic websites.

Let me explain.

There's a huge gap between a fully static and fully dynamic site and a lot of sites end up lumped into one even though they don’t fit perfectly.

What if only a small percentage of the content in a site changes periodically? Then you find yourself in a tricky situation. Do you build a static site knowing that you'll have to manually update some of the content? Or do you make the entire thing a dynamic site, even though most of it doesn't need to be?

There are also a lot of limitations to both static and dynamic sites that can be hard to resolve.

What if we need a site with some text content, some data from an API, and some other data in Excel spreadsheet? Tools like WordPress and Drupal can handle this, but the solutions are not great and often slow. I have had client sites where I basically implemented a makeshift version of Excel inside the WordPress admin dashboard, because that's how the client's data was structured.

Gatsby not only bridges the gap between static and dynamic sites, it also makes it so many of the limitations of static and dynamic sites aren't an issue anymore.

## The Real Value of Gatsby

As Gatsby grew, it picked up and incorporated GraphQL for its data layer and this is what really made Gatsby more than a static site generator. Because Gatsby uses GraphQL for its data layer, your data can easily come from anywhere. Literally. I've built a Gatsby site where MailChimp was the back-end and it’s not uncommon to see Gatsby sites built with data coming from APIs, Spreadsheets, AirTable, or any number of other tools for managing data.

This is the real value of Gatsby - you can generate a website that is fast and easy to maintain with data that comes from anywhere. Specifically, from the best tool to manage that data.

## Conclusion

Gatsby outgrew the static site generator label, but it also changed the way we need to think about building websites. For as long as I can remember, we've been thinking of websites as made up of content, when really they're made up of data and content is a type of data. That thinking limited us to content site generators, whether they were static or dynamic.

With Gatsby, our web site is the presentation of data, where ever that data is managed. Content data can be managed in a Content Management System (CMS) like WordPress, while panel-like data can be managed in an API (like Strapi or AirTable). You could even manage data for your site inside Google Sheets.

The point is this: with Gatsby, we're no longer confined to building either static or dynamic sites. Now, the parts of a site that need to be static can be, while the parts that need to be dynamic can be.

## Update: December, 2020

Sometime since this article was first published, Gatsby changed to describe it's self as, "One Front-end to Rule Them All." This is a little hyperbolic, but it agrees with the argument I made in this article.
