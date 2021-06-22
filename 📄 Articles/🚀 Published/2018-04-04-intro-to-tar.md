---
title: Intro to tar
slug: intro-to-tar
date_published: 2018-04-04T11:37:00.000Z
date_updated: 2021-04-13T13:00:27.000Z
tags: Productivity, Unix
excerpt: Tar is a great little utility for working with archives. It also happens to be very easy to pick up!
---

`tar` is a tool for taking a collection of files and folders and generating an archive. It was originally used for reading and writing archive files to and from tapes, so it was called Tape Archive - or `tar`, for short. That should give you a sense of how old the tool is!

Old as it is though, it is still really common for linux server administration.

## Background

I first needed to learn how to use `tar` at a previous job, where I was backing up legacy client websites from our linux servers. Turns out, that's something `tar` is used for frequently. That's because it creates an archive of a collection of files and *preserves all the file information*. Think of all that information you see when you run `ls -a`, `tar` preserves all of that in the final archive: the owner, user and group permissions, date of last modification, etc.

That makes `tar` archives really safe for back ups. Not only can you compress a large collection of files into a single `.tar` file that you can then copy locally, the archive preserves all the file information! It'll be so easy to restore the files from their archive.

## Getting Started with `tar`

Let's start by using `tar` to create a simple archive. Like many linux command line utilities, `tar` takes both *options* and *operations*. What's the difference?

**Operation:** A flag that tells a utility what action to perform.

**Option:** A flag that tells a utility how to perform some action.

One common *option* you may be familiar with is `-v`, or `--verbose`. The `-v` option tells a utility to use *verbose* output. A common *operation* you may be familiar with is `-c`, or `--create`.

`tar` has three commonly used operations:
OperationDescription`--create` (`-c`)Create an archive`--list` (`-t`)List the contents of an archive`--extract` (`-x`)Extract the contents of an archive
These are the most common operations, but there are others like `--append`, `--delete`, `--update`, and `--compare`. I'll discuss a few common options throughout the rest of this post.

## Creating an Archive

Okay, let's create our archive now! Pick a folder of files that you want to experiment with or make one up:

    cd sandbox
    mkdir tar-test
    cd tar-test
    mkdir folder
    touch folder/{one,two}.txt
    touch folder/{three,four}.json

Now to create our archive:

    tar --create --file=archive.tar folder

Boom! 💥 It worked! So what did we just do? `tar` is the utility we're using (obviously). The name of the operation we want to perform is `--create`. We have to pass in the name of the final archive, which is what `--file=archive.tar` is doing. Finally, we have to tell `tar` what folder we want to archive, so we finish with the relative path, `folder`.

The second two parts (`--file=archive.tar` and `folder`) are important. If we don't include the file for the archive, then the archive just gets output to the terminal, which is not super useful. If we don't include the folder or collection of files to archive then `tar` throws an error: `no files or directories specified`.

We can shorten that up a bit:

    tar -cf archive.tar folder

This will give you the exact same result (an `archive.tar` with the contents of `folder/`) because it is the exact same command as the one above above, just using the short names for the operation (`-c`) and option (`-f`).

Now, we are creating an archive but not a *compressed* archive. For that, we need the `--compress` flag (or `-z` for short). All together it's one of the following:

    # long version:
    tar --create --compress --file=archive.tar folder
    
    # short version:
    tar -czf archive.tar folder

An additional option you can use is `--verbose` (or `-v`), for verbose output. That will looks like this:

    # long version:
    tar --create --compress --verbose --file=archive.tar folder
    
    # short version:
    tar -czvf archive.tar folder

## Listing the Contents of an Archive

Listing the contents of an archive didn't seem like a very handy feature until I was working with really big archives of large legacy applications. The basic command for listing the contents of an archive is this:

    tar --list --file=archive.tar

The shortened version looks like this:

    tar -tf archive.tar

If you run this command on the sample folder from above, your output should look like this:

    folder/
    folder/four.txt
    folder/one.txt
    folder/three.json
    folder/two.json

A handy tip is that we can pass in some file path pattern as a second argument to narrow our results. For instance, we could do something like this to only get back the json files:

    tar -tf archive.tar *.json

It works for subdirectories as well!

## Extracting Files from an Archive

The operation for extracting files from an archive is `--extract` (or `-x` for short). The pattern is the same:

    tar -xf archive.tar

This command will extract all the contents of the archive. One of the things that's great about `tar` though is we can selectively extract files and folders. We can do that by just passing the path in as the second argument:

    tar -xf archive.tar folder/one.txt

## Conclusion

The three most common operations you'll need to perform with `tar` are creating an archive (with `-c`), listing an archive (with `-t`) or extracting an archive (with `-x`). But there is a lot more you can do with `tar`!

For instance, you can append files to an existing archive. I found this useful when I was backing up websites with `tar` - I could just append a `.sql` dump of the database rather than create a whole new archive when I had forgotten to include it in the first place. If you create an archive and then some of the original files change, you can update your existing archive with `--update` or `-u`. Finally, you can compare the contents of your archive with the contents of the original files using the `--compare` (or `-d`) operation. That's helpful for seeing if you need to update your archive!
