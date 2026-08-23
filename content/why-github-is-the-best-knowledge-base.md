# Why GitHub is the best knowledge base

Over the past few months, I've been using GitHub as my main knowledge base, and it works really well - especially in combination with coding agents like Claude Code.

## How I use it

To me, it's kind of a Notion replacement. Instead of opening up a Notion document, I just create a new repo or find an existing private repo where I can put my notes. I dictate my thoughts and develop my notes there, and if I have some research to do, I let Claude Code do the research and update those repos.

I also have repos for skills. If I have to repeat the same type of work over and over again, it's nice to be able to have that in a skill format so I can reuse those workflows.

Searching is easy too. I even created a system for it: cloning all my repos into a single folder and running ripgrep over that. I wrote about it in [The missing private GitHub search](the-missing-private-github-search.md).

## Virtually unlimited storage

Turns out there's pretty much no limit to how much data you can store.

There is a per-file limit, but you can get around it. GitHub rejects any regular git commit with a file over 100 MB, so big files can't go into the repo itself. Instead, you attach them to a GitHub release: each release asset can be up to 2 GB, and there's no limit on the total.

For anything over 2 GB, you split. I recently needed to store an 11.6 GB video:

```bash
# split into parts under the 2 GB cap, and save a checksum
split -b 1900m video.mov video.mov.part-
shasum -a 256 video.mov > video-sha256.txt

# upload the parts as release assets
gh release create archive --notes "original video, split into parts"
gh release upload archive video.mov.part-* video-sha256.txt
```

And to get the file back:

```bash
gh release download archive --pattern 'video.mov.part-*'
cat video.mov.part-* > video.mov
shasum -a 256 -c video-sha256.txt
```

## Why now

It didn't make sense before, because it would have been too much work to create repos, manage them, and search through them. Coding agents just make all of that so much easier. I highly recommend it.
