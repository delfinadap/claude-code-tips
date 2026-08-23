# Why GitHub is the best knowledge base

Over the past few months, I've been using GitHub as my main knowledge base, and it works really well - especially in combination with coding agents like Claude Code.

## How I use it

It's kind of a Notion replacement. Instead of opening up a Notion document, I just create a new repo or find an existing private repo where I can put my notes. I dictate my thoughts and develop my notes there, and if I have some research to do, I let Claude Code do the research and update those repos. I also have repos for skills, so workflows I repeat often are reusable.

Searching is easy too. I even created a system for it: cloning all my repos into a single folder and running ripgrep over that. I wrote about it in [The missing private GitHub search](the-missing-private-github-search.md).

## Virtually unlimited storage

Turns out there's pretty much no limit to how much data you can store. There is a per-file limit: regular git commits reject files over 100 MB, and release assets cap at 2 GB per file. But you can get around it by splitting.

I recently needed to store an 11.6 GB video. I split it into six parts with `split -b 1900m`, uploaded the parts as release assets on a private repo, and saved a SHA-256 checksum alongside them. To get the file back: download the parts, `cat` them back together, and verify against the checksum.

## Why now

It didn't make sense before, because it would have been too much work to create repos, manage them, and search through them. Coding agents just make all of that so much easier.

I highly recommend it.
