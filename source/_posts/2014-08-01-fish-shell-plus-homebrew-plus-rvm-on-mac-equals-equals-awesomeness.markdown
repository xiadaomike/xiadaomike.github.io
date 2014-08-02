---
layout: post
title: "Fish Shell + HomeBrew + RVM + Iterm2 on Mac = Awesomeness"
date: 2014-08-01 02:33:19 -0700
comments: true
categories: [tech, tips, iterm, mac, fish, brew]
keywords: tutorial, setup, mavericks, mac, fish, homebrew, brew, iterm, rvm
description: A tutorial on how to setup fish shell with homebrew and rvm on osx mavericks.
---

A tutorial on how to setup fish shell with homebrew and rvm on osx mavericks.

Last week my friend James showed to me the autocompletion feature in fish shell
and I was impressed. It is a feature that you may never thought about until one
day you tried it and can't imagine life without it. In the last few days, I've
been trying to get homebrew and rvm working on fish shell. So I thought maybe
this would turn into a good blog post to share my setup with others.

This post is based on the wonderful article in German [here](http://blog.detmud.me/2013/05/mac-homebrew-fishfish-rvm/).

<b>1. First, install command line development tools by running:

~~~ bash
xcode-select --install
~~~

<br>2. To install Homebrew, simply do:

~~~ bash
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
~~~

<br>
Make sure to run `brew update` and `brew doctor` before any of the
following steps.

<b>3. To install fish shell with homebrew, run:

~~~ bash
brew install fish
~~~
<br>Do not set fish as default shell yet, we will do this at the end.

<b>4. Next, we install rvm manually. (I found this way of installation to be the
    cleanest one):

~~~ bash
mkdir -p ~/.rvm/src && cd ~/.rvm/src
git clone --depth 1 git://github.com/wayneeseguin/rvm.git
cd rvm && ./install
~~~

<br>5. Set up fish shell configuration files with oh-my-fish. To install, run:

~~~ bash
curl -L https://github.com/bpinto/oh-my-fish/raw/master/tools/install.fish | fish
~~~

<br>The config file is located at `~/.config/fish/config.fish`{:lang="bash"} You may find this
[config](https://gist.github.com/wilhelm-murdoch/6162503) useful. It configures
the fish shell so that every time when you enter a git repository, the current 
branch will be shown. Also, it includes an `iterm` scheme that I personally
like a lot.

<b>6. Make sure to add the following lines into your `config.fish` file:

~~~ bash
set fish_plugins brew rvm
set -x PATH /usr/local/bin /usr/local/sbin $PATH
rvm > /dev/null
~~~

<br>7. Finally, setup fish as your system and default shell:
Add `/usr/local/bin/fish` to `/etc/shells`, and then type into your
terminal emulator:

~~~ bash
chsh -s /usr/local/bin/fish
~~~

<br>Enter your password if prompt and restart your terminal emulator. Voila! How
beautiful this is.
