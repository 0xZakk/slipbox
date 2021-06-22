---
title: Write Like Farnam Street
slug: write-like-farnam-street
date_published: 2021-01-24T00:00:00.000Z
date_updated: 2021-03-05T13:34:06.000Z
tags: Writing
excerpt: What does it take to be a great writer? To find out, let's look at some data.
---

I want to be a successful writer. But I don’t know how.

My natural inclination when faced with a problem like this is to read around and ask questions. I’m looking for advice from someone who has achieved what I want to achieve. When I find it, I can weigh it and test it. If it seems promising, then the best thing to do is act as if it’s true.

Last year, I took David Perell’s course Write of Passage. One of the core principles of the course is this:

> B+ content and A+ consistency is the winning formula … Most of the value comes from consistency, not content.

The important point that David is making is one of semantics: great writers aren’t Great Writers™. They’re good, consistent writers.

But I don’t buy it.

I mean, you expect me to knowingly publish a B+ article?

I’ll have you know that I got not one, but two high school diplomas. Both. Honors. In college, I wrote my Senior thesis during my Sophomore year - it was almost 100 pages long. And while everyone else studied abroad in Paris or Rome, I did my first year of law school.

B+ content - I think not!

## Method

What follows is a science report of sorts on becoming a successful writer. David’s theory is: becoming a great writer requires publishing good work consistently over time. If that were true (which it isn’t) then we should be able to prove it by looking at a great writer and see this trend manifest in their work. When in doubt, test it out.

I’ve examined Shane Parish’s blog, Farnam Street, as an example. I really admire Shane’s work and would love to carve out a space for my writing on tech, much in the same way Shane has for investing.

To disprove David’s theory, I used a Linux utility called `wget` that recursively downloads the contents of a website. It took a while to run, but it pulled everything at [fs.blog](http://fs.blog/). Once the site was backed up on to my hard drive, I could write and run scripts on the HTML as a way of “querying” the data.

I wrote 4 scripts to collect data from the site’s codebase. The scripts did the following:

- Created a histogram of posts per month
- Created a histogram of posts per year
- Counted the words in each post
- Counted words in a `<blockquote>` versus in another element

## Analysis

I’m specifically looking to show a couple things about writing and becoming a successful author online:

- I don’t actually have to post all the time (Post Frequency)
- My articles have to be long and in-depth in order to provide value (Post Length)
- Everything I publish has to be completely original (Post Originality)

We’ll look at each of these in turn.

## Post Frequency

The first things I did with the data was look at posts-per-month and posts-per-year for the 12 years that Farnam street has been around.

Here is the number of posts per year:
![](https://zkf.io/content/images/2021/02/fs-posts-per-year.png)
Pretty incredible if you ask me. You can see that the first three years were pretty mellow, at 2-4 posts per month. Then from 2012 to 2017, Shane kicked it into overdrive and published 9 to 16 articles per month (one every couple of days). The pace mellows back out a lot in 2018 and for the last 3 years Farnam Street has published 40-47 posts per year.

A piece of the puzzle that we’re missing here is Farnam Street’s analytics. How much growth happened in the period between 2012 and 2017? While I can’t answer that question, we know what Shane’s reach is now. So unfortunately I have to admit that David might be right on this point. Shane’s success and publishing history supports the idea that publishing consistently and frequently is part of becoming a successful writer.

What if about posts per month?

Here is how Shane’s publishing frequency looked for 2011:
![](https://zkf.io/content/images/2021/02/fs-2011-post-per-month.png)
The high variance is what immediately jumps out to me. You have May, when Shane only published one post, and August, when Shane published nine posts. I'm not going to call this a win yet, but things are looking better for me.

Here is the publishing frequency by month for 2013, Shane’s most prolific year:
![](https://zkf.io/content/images/2021/02/fs-2013-post-per-month.png)
There’s still a pretty high amount of variance (27 posts in the highest month and 10 in the lowest) but the average is significantly higher (15.25 posts per month in 2013 versus 4.6 posts per month on average in 2011).

What about last year?
![](https://zkf.io/content/images/2021/02/fs-2020-post-per-month.png)
An average of 3.91 posts per month. But notice how little it varies from month to month?

I wonder when Farnam Street has seen the most growth. Is it during years like 2013, when Shane is publishing something every couple of days? I also wonder which is more important: consistency or frequency. In 2020, Shane published 3-5 posts every month (very consistent); in 2013, Shane published ten or more posts every month (high frequency).

I can’t answer questions at that level of granularity without access to his analytics. But we can generalize and say that frequent and consistent publishing (>40 posts per year for many years) is necessary for growth.

I’ll concede this point to David.

## Post Length

Surely being a successful writer online requires publishing long, nuanced articles. You have to explore every nook and cranny of a subject and any possible edge cases in your argument. Leave no stone unturned and all that!

Here’s how the articles on Farnam Street break down by word count:
![](https://zkf.io/content/images/2021/02/fs-post-length.png)
There is a very clear trend here: posts tend to be short. Half (~51%) of the posts on Farnam Street are less than 1,000 words and the vast majority (~85%) are less than 2,000 words. Only about 15% are longer than 2,000 words.

David gets this point too.

An assumption that many new writers have, myself included, is that the things you publish have to be long, well-researched, nuanced, and in-depth in order to be valuable. If you think about it though, if that were true no one would know who Seth Godin is and Farnam Street probably wouldn’t have the reach that it does today.

I went back through and found that many of my favorite articles were some of the longer ones (like [this one](https://fs.blog/2018/01/john-boyd-ooda-loop/) on the OODA Loop - 3,429 words). That said, the first articles I read on Farnam Street were all among the shorter ones.

This supports the idea that great writers are those that publish good work consistently. David is two for two. I see length as a proxy for depth and comprehensiveness (i.e. how Great™ is the article). Instead, the data shows that articles should be digestible. Focus on consistently publishing digestible articles over comprehensive ones. Mix in articles with more depth as you have the inclination and time.

## Post Originality

I really thought that this is where I would I would see a win. The platonic idea of a great writer is one who shares completely original work. You know, as part of their greatness.

That didn’t really hold up in the data either:
![](https://zkf.io/content/images/2021/02/fs-original-v-quoted.png)
As you can see in the graph above, Farnam Street makes pretty liberal use of quotes. There is a sort-of Barbell trend where the two largest categories are (1) posts that are mostly original (<25% quoted text) and (2) posts that are mostly quoted (>75% quoted text). It’s not a strong trend though since Shane’s articles are everywhere on the spectrum.

I guess the articles I publish don’t need to be completely original in the way I thought. After looking more closely, I think it’s important that your articles are useful (regardless of how original they are). One post that is mostly quotes is the transcript of [David Foster Wallace’s commencement speech](https://fs.blog/2012/04/david-foster-wallace-this-is-water/). It’s 99% quoted text, but I’ve read it on Farnam Street at least 3 times. Another post I’ve read multiple times is [The Value of Probabilistic Thinking](https://fs.blog/2018/05/probabilistic-thinking/) - it’s 2,671 words long and doesn’t have a single quote.

Both are on opposite ends of the originality spectrum. Both are good.

## Weaknesses and Considerations

Before I wrap up with this study with what these findings mean, there are a couple of things to keep in mind about this data.

**Word counts are approximate.** After downloading the HTML for the site, I wrote a script that isolated the text of all the posts. I then wrote a Python script that used a regular expression to count the words in each article. This is a good, quick approach. But it is not exact. For instance, you and I would count six words in the sentence, `"Hello world, it's a wonderful life."`, but this regular expression counts seven because `it` and `s` in `it's` is counted as two words, rather than one.

**Articles aren't the only content Farnam Street produces.** They also produce a podcast and a newsletter. The thesis is that consistently producing good content over a long time period is necessary for becoming a successful writer. By only looking at one type of content, we are only getting an approximate answer and not the whole picture.

**My IP was blocked by Farnam Street.** This is unfortunate but something I should have expected. I'm confident that I was able to download the whole site (including every blog post) before I was blocked. However, because I was blocked, I can't verify this completely. Side note: if you enjoyed this analysis, please share it and tag [Shane](https://twitter.com/ShaneAParrish). Hopefully then he will unblock my IP so I can keep reading Farnam Street. Otherwise I may have to move.

## Parting Thoughts

One of my favorite quotes is, "In God we trust. All others bring data." This has been a fun dive into some data from a very popular blog by a great writer. While it does not completely prove the thesis, I have to tuck my tail between my legs and admit that it is supported. Becoming a successful writer online seems to be about publishing good work consistently over a long time period.

More specifically, we can see from the data that consistently and frequently publishing something useful does not necessarily mean publishing something long, in-depth, or completely original. David Perell actually had an interesting take on this recently, when he noted that Yuval Noah Horari wrote one of the most successful (and perhaps most important) books of the last few years, Sapiens, without doing any original research ([source](https://twitter.com/david_perell/status/1353190662343192583)).

Another of my favorite quotes is, "The person with dirty hands is right." David Perell put forward the thesis I examined here. What makes him credible is that he is himself a successful writer — his hands are dirty. David publishes two newsletters, a podcast, a couple of short- to medium-length articles every week, and an in-depth article every couple of months and he has done so for a couple of years now.

I’ve weighed David’s advice and, given what we learned from the data on Farnam Street, it seems promising. Therefore, the best thing for me to do is to get my own hands dirty and publish a lot. It’s time to act as if this advice is true and see what happens.

Finally, I’d like to say that this was all for science so, Shane, if you’re reading this, please unblock my IP address. ❤️

*Update: I just moved. (February 4, 2021)*
