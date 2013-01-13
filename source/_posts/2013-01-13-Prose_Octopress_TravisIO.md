---
layout: post
title: "Prose.io + Octopress + Travis-CI + GitHub Pages = ♥"
comments: true
categories: 
published: true

---

I wanted to have nice workflow to write to my [octopress](http://octopress.org)-powered blog. So idea was:

1. I’m editing or creating post in [Prose.io](http://prose.io) or just in GitHub’s web editor.
2. Wonderful open-source free hosted continious integration server [Travis-CI](https://travis-ci.org/) builds my Octopress blog and pushes generated version back to [GitHub Pages](http://pages.github.com/)


<!-- more -->

## Nice settings for Prose.io to edit Octopress blog

First, I need Prose.io to be nice with octopress. I added these lines to end of `_config.yml` of Octopress blog:

``` yaml
#prose.io settings
prose:
  rooturl: "source"
  metadata:
    "source/_posts": |
      layout: post
      title: "Title"
      comments: true
      categories: 
      published: true
```

Thats exactly what it looks like. It tells Prose.io, which directory to load, and specifies Octopress’s metadata.

## Travis

It’s a pain. This is my `.travis.yml`:

{% gist 4522846 %}

It’s kinda complex :) You just have to put your encoded SSH key instead of mine (`all - secure:` lines) and put your repo address (`- REPO=`). To encode SSH key for Travis I used this gist:

{% gist 4242707 %}

It works like magic!
