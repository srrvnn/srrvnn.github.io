---
layout: post
title: Contributing.md
published: true
categories:
---

Contributing to open source is pleasure. It's been four years of exciting evenings, refactor weekends and sneak commits. JK. My OSS contributions just began with the &mdash; Hacktoberfest.

4 PRs == One Free T-Shirt. Sounded like a fair deal to me.

#### Hacktoberfest?

![Image of Hacktoberfest Banner](http://i.imgur.com/BQDw50T.png)

It must have been someone on Twitter, who introduced Hacktoberfest to me. To encourage people to contribute to open source projects, DigitalOcean promised a free tee to anyone who *merely opens* four pull requests through the month of October.

I have spent several evenings gaping at clean, well written projects, and [@mdo](https://github.com/mdo) has been my OSS hero. But, I felt too comfortable being a consumer. The only [other time](https://github.com/karma-runner/karma-jasmine/pull/92) I made the leap and contributed was when karma-jasmine seemed to be incorrectly extract test failures from the error stack, and I did not want our test reports to reflect that a hungry rat was around.

To me, contributing was like a gravity. All it needed was a little push.

#### PR One: Hello Habitica!

I filtered projects by JavaScript and found HabitRPG/habitrpg. Great. An all-JS stack.

It took a couple of minutes to get habitrpg up. I found an issue asking to filter the list of chat messages to remove the flagged ones unless the user was an administrator. Easy Peasy.

Testing took longer than expected. I tweaked the message creating function to always add a flagged message (evilchat.io &mdash; *tags as idea, checks route 53)*. Smartly, flagged wasn't a propery that could be dry during create. And the UI wouldn't allow me to flag my own message. I tweaked the UI to always show the flag icon, and was able to flag and verify.

```javascript
if (!user.contributor.admin) {
  group.chat = _.filter(group.chat, function(message) {
    return !message.flagCount || message.flagCount < 2;
  });
}
```

As of Nov 4th, [this](https://github.com/HabitRPG/habitrpg/pull/6065) is my first pull request and it's been merged. (Talk about little happiness)

#### PR Two: 350 / 350

I was a little more ambitious. I wanted to add ES6 to the JS section of learnxinyminutes.

I had bookmarked [@bevacqua](https://github.com/bevacqua)'s excellent [ponyfoo.com summary](https://ponyfoo.com/articles/es6) of ES6 in 350 Points for a train ride.

I had to, had to read the ES6 in depth articles on ponyfoo to get a clear picture of the bad boys in ES6 (symbols, iterators and proxies) and then I came up with [this pull request](https://github.com/adambard/learnxinyminutes-docs/pull/1905). A very satisfying one.

#### PR Three: Tricky Refactor.

mustache.js wanted someone to refactor a ~125 line function. This was tricky with the code already being well refactored. I studied a similar refactor pull request, and the function repeatedly.

Moved coherent blocks of code outside the function into one of their own, while trying to keep coupling low. Ideally these functions would perform one task thus making their testing a breeze.

[janl/mustache.js: refactor parseTemplate()](https://github.com/janl/mustache.js/pull/527)

mustache.js had a robust test suite, so I could gain confidence in a breeze.

#### PR Four: Finish him!

I added a Less page to learnxinyminutes relying heavily on a PR by another contributor for a Sass tutorial. The docs came in handy and I promised I will revisit [this one](https://github.com/adambard/learnxinyminutes-docs/pull/1994) soon.

---

This is only a step in the direction of contributing and building open source software. It was exciting to take up a challenge, and live through it. And now: :tada: :tada:

![Image of Verification Script](http://i.imgur.com/XxnBamZ.jpg)

Will update with *the* shirt when it arrives!

