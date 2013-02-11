---
layout: post
category: Tools for Making Software
---
{% include JB/setup %}

It happened several times that a library appealed to me just for a few handy methods. But depending on a library is an act of commitment. And it's not a marriage-like commitment, this will be a one way commitment, your code won't change that library but the reverse will be true. And getting rid of that dependency will only get more difficult with time.

In that post, as the title promises, I'll advocate code pasting with a twist. But first I'll just sum up what you rely on when choosing the library path:

&rarr; **Trust**, when you download code which you don't own, you have to trust that the person who wrote it knew what she or he was doing. The basic functionality has to be reliable. Edge cases have to be taken care of. As a developer, you know these things are hard, and you know also that you've been let down by libraries before.

&rarr; **Luck**, you have to be somewhat lucky to find a library that does exactly what you need. Most of the time it will do something approaching your need and you'll have to deal with it with some wrapper and inefficient code to get it working.

Ok let's say you got trust and luck in that smiley library to which you couldn't resist. Now you're gone for a life long (at least) reliance on:

&rarr; **Maintenance**, you'll hope that it will be maintained, at least from a bug fixing point of view. You could do it yourself, but do you have time for that? Remember, you only wanted a few methods from that library.

&rarr; **Relevance**, you might fall for another much cuter library when the relationship is already quite deep. Not uncommon.

&rarr; **Public repo publication**, I wouldn't use a library not published on a public repo, it's just too much hassle.

&rarr; **Backward compatibility**, this is the most tricky one. Anything could break when you change versions, even if the method signatures is the same.

&rarr; **Compatibility with other libraries**, can be really painful. Why can't all libraries be nice to each other?

When you use a library, you have to be aware of all that.

And as a library author you have to be aware of all the users who are aware of all that. Daunting. That's what makes me think that open source libraries should be the responsibility of mainly companies and heavily invested developers. But still, I really want to enjoy all the fantastic common knowledge generated by the millions of developer ready to share their code. And I think the simple copy and paste will do just fine for the majority of these cases. It is so much easier, for the authors, and the developers. You-author write a lovely generic piece of code, make it public, and still can modify it at your heart's will. You-user copy that piece of code, put it in your house framework and that's it, it's yours.

Pasting code is good because:
- you can tailor that code to your exact needs
- you can later modify the code whenever and however you want

**BUT**, and that's where I want to bring you, Dear Reader, pasting is only good when:
- you understand what you copy
- the piece of code is reliable

And there is no service to my knowledge that goes in that direction.
One might say "use a paste bin!" but I'd answer that you can't trust a piece of code coming from a paste bin.

What that service of my wildest dreams would do:
- ask the developer to provide tests with 80% coverage mandatory (verifying other metrics would be nice too)
- when you copy the code, don't forget to copy the tests too (look, boss, code coverage is up!)
- tests running live, with a green or red flag telling me if that code runs
- relevant search
- double display, with the tests on the left and production code on the right
- a limit on the number of files and lines (go put your code in a full blown library if you go past that limit)
- cool stats like the number of people who copied the piece of code
- good old comments to help making that code better

To summarize, that service would be a cross between a gist.github.com, TDD and an integration server. And as it is a bit of dream, I'll push even further by adding social features geared toward safer, high quality code.

**Am I the only one out there who wants that service?**