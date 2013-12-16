---
layout: post
title: "Your local changes to the following files would be overwritten when running brew update
"
description: ""
category: ""
tags: []
---
Tonight while running brew update on my Mac, I received the following error
messages:

    brew update && brew install phantomjs
    error: Your local changes to the following files would be overwritten by merge:
      Library/Formula/imagemagick.rb
    Please, commit your changes or stash them before you can merge.

To fix the problem, I had to run the following:

    cd `brew --prefix`
    git remote add origin https://github.com/mxcl/homebrew.git
    git fetch origin
    git reset --hard origin/master

This was documented at the homebrew project within Github,
https://github.com/mxcl/homebrew/issues/11448#issuecomment-4959157.
{% include JB/setup %}
