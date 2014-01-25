---
layout: post
category: Tools for Making Software
---
{% include JB/setup %}

It happened several times that a library appealed to me just for a few handy methods. But depending on a library is an act of commitment. And it's not a marriage-like commitment, this will be a one way commitment, your code won't change that library but the reverse will be true. And getting rid of that dependency will only get more difficult with time. 

If you want a library to rely on for a structural service like dependency injection or logging or web services, I more than fully agree with the library solution. These services are either generic or standards or both. What follows is for functionalities which you have the choice between writing them and finding them somewhere else, be it a library or sample code to copy and paste.

In this post, as the title promises, I'll advocate code pasting, with an important twist. But first I really want to emphasize how big is the commitment when you choose to depend on a library. Here are the things you will rely on:

**Trust**, when you download code which you don't own, you have to trust that the person who wrote it knew what she or he was doing. The basic functionality has to be reliable. Edge cases have to be taken care of. As a developer, you know these things are hard, and you know also that you've been let down by libraries before.

**Luck**, you have to be somewhat lucky to find a library that does exactly what you need. Most of the time it will do something approaching your need and you'll have to deal with it with some wrapper and inefficient code to get it working.

Ok let's say you got trust and luck in that pretty library to which you couldn't resist. Now you're gone for a life long (at least) reliance on:

**Maintenance**, you'll hope that it will be maintained, at least from a bug fixing point of view. You could do it yourself, but do you have time for that? Remember, you only wanted a few methods from that library.

**Relevance**, you might fall for another much cuter library when the relationship is already quite deep. Not uncommon.

**Public repo publication**, I wouldn't use a library not published on a public repo, it's just too much hassle.

**Backward compatibility**, this is the most tricky one. Anything could break when you change versions, even if the method signatures is the same.

**Compatibility with other libraries**, can be really painful. Why can't all libraries be nice to each other?

When you use a library, you have to be aware of all that.

And as a library author you have to be aware of all the users who are aware of all that. Daunting. That's what makes me think that open source libraries should be the responsibility of mainly companies and heavily invested developers. But still, I really want to enjoy all the fantastic common knowledge and pieces of code created by the millions of developer ready to share. And I think the simple copy and paste will do just fine for the majority of these cases. It is so much easier for the authors, and the developers. You-author write a lovely generic piece of code, make it public, and still can modify it at your heart's will. You-user copy that piece of code, put it in your house framework and that's it, it's yours.

Pasting code is good because:
- you can tailor that code to your exact needs
- you can later modify the code whenever and however you want

**BUT**, and that's where I want to bring you, Dear Reader, pasting is only good when:
- you understand what you copy
- the piece of code is reliable

And there is no service to my knowledge that goes in that direction.
One might say "use a paste bin!" but I'd answer that you can't trust a piece of code coming from a paste bin.
Another will say copy from "Stackoverflow" but I'd answer that pieces of code posted there are illustrative at best.
And someone else will come back to the libraries solution "that's why we have libraries with feature and bug fixing" but I'd answer that I don't need 9/10 of your library and bear its cost for the lifetime of my software (with all the arguments already cited above).

I want copy and paste with a reliable source. How many of you have looked for a standard requirement and looked at how someone did the same functionality in his open source project? And then tried to paste that solution in there own project? I'm sure you ended up starting from that piece of code you painfully extracted before rewriting it according your specific needs. That's what I've done a few times anyway.
This is a tedious process. And where there is tediousness there is potential for better. Github provides libraries, Gist is not a trustable source, Stackoverflow gives you answers, not code. There is space for another service.

What that service of my wildest dreams would do:
- Ask the developer to **provide tests** with \[arbitrary\]% coverage mandatory (verifying other metrics would be nice too).
- Tests running live, with a green or red flag telling me if that code runs at the moment.
- Relevant search.
- When displaying the code, tests are shown on the left and production code on the right.
- A limit on the number of files and lines (go put your code in a full blown library if you go past that limit)
- Cool stats like the number of people who copied the piece of code
- Good old comments to help making that code better
That's it for the basic service.

One question I really have difficulties to answer is whether or not the piece of code can depend on a non standard library of the language. I think the service would be far more useful it was possible, but it would be slightly ironic, wouldn't it?