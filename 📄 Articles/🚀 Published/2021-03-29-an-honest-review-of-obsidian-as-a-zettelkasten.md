---
title: An Honest Review of Obsidian as a Zettelkasten
slug: an-honest-review-of-obsidian-as-a-zettelkasten
date_published: 2021-03-29T13:39:23.000Z
date_updated: 2021-03-29T13:39:23.000Z
tags: Productivity, Writing
excerpt: I spent the last few months using Obsidian as my primary note-taking tool. Here, I walk through the things I love about it.
---

## Introduction

For the last few weeks, I have been using Obsidian as my primary Zettelkasten. While I haven’t committed to making the transition permanent, I did want to give Obsidian an earnest shot. So I downloaded an archive of my Zettelkasten from Roam and migrated it into Obsidian.

I have been really pleasantly surprised by Obsidian. It does get a lot of things right. While I haven’t committed to making the transition permanent, I do see why people love Obsidian so much. It has a number of really helpful characteristics to it, all without that rough-around-the-edges feeling that Roam can have.

While I love Roam, there are some things that aren’t quite right about it. Speaking honestly, I’m also worried that the Roam team is too focused on shipping a lot of fancy new features and not focused enough on the boring, but necessary work of (a) improving the three to five most important features or (b) shipping features that are well built.

For instance, it really bothers me that I still can’t bold highlighted text, but there are now spaced-repetition systems, charts, drawings, tables, drop downs, and kanban boards in Roam. Each of these features is really cool. But for every single one of them, there is at least one thing that is slightly annoying about the way they work. I love drop downs, for example, but they totally mess up Linked References because every option in the drop down is a reference, not just the one that’s selected. It’s like every new feature has a promising start, but the execution is an after-thought.

I went into my exploration of Obsidian knowing that no tool will every be perfect. But I wanted a clear sense of what the trade-offs were.

## Obsidian: The Good

### Flat Files

I found this to be the biggest advantage of Obsidian: it uses flat markdown files that are saved to your computer’s file system. When I first set up my Zettelkasten in Obsidian, I created my Vault (the Obsidian equivalent of a Graph) in an iCloud folder. Instantly, my notes were backed up, synced across all my devices, and accessible from my phone.

The fact that Obsidian uses flat files also makes your notes easier to work with. Migrating my Zettelkasten from Roam to Obsidian was pretty easy: I downloaded a backup of my Roam database as markdown, then used my Mac’s built-in file system tools to move all my notes into different folders for Literature, Reference, and Permanent notes. You can do all of this and Obsidian will keep track of page links and references too.

As a software engineer, the fact that Obsidian uses flat files also opens up a lot of really interesting possibilities. For instance, I downloaded all of Farnam Street [for my article on Shane Parish](https://zkf.io/write-like-farnam-street/). I could potentially write a script that pulls articles from websites I regularly visit, converts them to markdown, and then adds them to my Reference notes. The unlinked references feature suddenly becomes extremely valuable.

Programmer or not, the potential for automating with flat files should be seen as a huge advantage. For instance, you could set up your vault in a Dropbox folder to have it automatically backed up. You could also set up a Zapier integration between Readwise, Evernote, and Dropbox so all your highlights automatically get added to your vault as markdown files. You could also set it up so that moving a note into a specific subfolder of your Dropbox vault automatically publishes it to your website.

### Plain and Simple Markdown

I love writing markdown. So much so that an early iteration of my Zettelkasten, before I discovered Roam, used Vim and a folder of notes on my file system. After years of using it, Markdown feels really natural and comfortable for me. The fact that Obsidian uses plain and standard markdown made it instantly familiar.

But the most important advantage of using standard markdown is that your writing is portable. That’s the whole point of using markdown. Because Obsidian uses standard markdown, I don’t have to translate my writing to use it elsewhere, like publishing it to this blog.

### Link Styles

I adore this feature of Obsidian. It not only addresses a pain point of writing in Roam, but it does so flawlessly while giving me functionality I didn’t know I would love and need.

Creating links in Roam is very easy, but those links are clunky. You can’t incorporate the link into the flow of a sentence because the content of the link is the page’s title. Instead, I often put links at the end of a sentence, like a citation.

I didn’t see that as an annoyance until I used Obsidian.

You can create page links in Obsidian and they work just as well as they do in Roam. But you can also specify the link text in Obsidian by using a pipe (`|`) after the page reference. This means you can link to a page without breaking the flow of your sentence:
![](https://zkf.io/content/images/2021/03/Screen-Shot-2021-03-29-at-9.13.57-AM.png)
![](https://zkf.io/content/images/2021/03/Screen-Shot-2021-03-29-at-9.13.51-AM.png)
It sounds small. But coming from Roam I’m used to features having small annoyances, not small delights. Setting the link text makes reading my notes a lot easier and makes linking (Roam’s key advantage over other note-taking apps) feel more natural.

### Speed

Obsidian is blazing fast. The start up time is relatively minimal and the jump time from note to note is practically instantaneous.

### Better Page Templates

The templates in Obsidian are amazing. I almost made the switch on this feature alone.

Obsidian comes with built-in support for templates. If you need something fancier, you can use one of the community plugins. But I found the built-in solution worked really well. Templates combined with the flat-file nature of Obsidian is a really killer combination.

Here is a screenshot of my template for Reference notes:
![](https://zkf.io/content/images/2021/03/Reference-note-template.png)
Notice that the metadata is on top, followed by the summary, a list of literature notes, and then the highlights This isn’t very different form how I construct Reference notes in Roam.

Compare that to my template for Literature notes:
![](https://zkf.io/content/images/2021/03/Literatuere-note-template.png)
The metadata for the note comes after the content. Here you can see examples of both:
![](https://zkf.io/content/images/2021/03/Reference-note-example.png)
![](https://zkf.io/content/images/2021/03/Literature-note-example.png)
These templates make my notes really easy to scan or read and they give me a lot of control of the information in a note.

You can sort of achieve the same thing in Roam with templates. But the big issue with Roam is, again, everything is only pretty-well implemented. I have to make a lot of trade-offs in how I construct page templates in Roam so that my notes are still usable with other features (like queries). For example, I would love to break our the note-type link from the category/area links in my notes, but then I wouldn’t be able to query for literature notes about a specific type:
![](https://zkf.io/content/images/2021/03/Screen-Shot-2021-03-26-at-9.42.30-AM.png)
You can see here, the first like gives me the type of note (In this case, a Literature note), followed by a pipe that acts as a separator, then the relevant category/area links. This is annoying, but I have to do it in order to make page queries work.

## Conclusion

After a few months of use, I did come to really appreciate Obsidian. I did write a lot and I continued to create a lot of notes. There are a number of features of Obsidian that are really well thought out and implemented and it does make for a really great writing and note-taking tool.

But I won’t be switching over to Obsidian permanently.

Despite its flaws, Roam is still the best tool for thinking and outlining. It’s so fluid and seamless to work with text and to bring ideas together. I imagine Nicholas Luhman shuffling his notecards into an outline. My goal is to achieve a digital version of that and the experience of dragging blocks of text around in Roam is more similar to it than anything Obsidian currently offers.
