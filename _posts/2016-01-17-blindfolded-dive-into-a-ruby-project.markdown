---
layout: post
title: Blindfolded dive into a Ruby on Rails Project
published: false
categories:
---

This is going to fun.

I just took over a Ruby on Rails project, and I have no clue about Ruby on
Rails. For the next however-minutes-this-takes: I am going to try to run this
project locally.

## starting at README.md

Unfortunately, all the README.md asks of me is to run db migrations, and db
seeding. A quick google search for 'How to run a Ruby applications' tells me
I need Ruby, RubyGems and SQL3Lite. `brew` to the rescue.

## install Ruby

Now, I seem to have two versions of ruby (from `which -a ruby`), and I need to
setup the latest version to run when I type `ruby`. Enter 'rvm'. After the
convoluted install (not homebrew, i.e.], `rvm list` doesn't list the two
versions `which -a ruby` does. Do I have to install ruby via rvm again? Really?
I decide to jump out of the DFS.

## install RubyGems and ~~sqllite3~~ sqlite3?

This: http://guides.rubygems.org/, is a wonderful read.

So, running `gem` looks like I have it already. Maybe it comes with Ruby.
Similarly running `sqlite3 --version` says I have version 3-something already.

## install rails?

I was going to, then I looked at a `Gemfile` that had a rails version listed.
Maybe some command will install everything in this file on my machine? Searching
for this on Google takes me one Bundler.
`gem install bundle` and `bundle install` follow.

## Make sure ... succeeds before bundling.

Two years ago, I heard my friend spend one hour on this issue. Here it is, now.
Fails again, while checking for pg_config. WTF is a pg_config?

SO tells me I have to reinstall postgresql. In my case, I had to install it.
`brew install postgresql`. Yay!

## Migrations are pending.

Good boy RoR tells me migrations are pending. Now I'll do:

db:migrate

## Getting this to AWS.

I found a How to Deploy a rails app on aws docs, and got started. Everything
looks good until I realize the article didn't care about a database.

it looks like i can use eb create with a -db.engine option, and that's what is
happening now.

And that's failing as well. I need to setup aws to know that it is running in
production so it knows where to look for the database, and I have no idea how
that is done.


