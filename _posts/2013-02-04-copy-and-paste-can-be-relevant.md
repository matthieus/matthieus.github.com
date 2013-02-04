---
layout: post
category: idea, open source
---
{% include JB/setup %}

Copy and Paste can be relevant

Pasting code is good because:
- now you can tailor that code to your exact needs
- because depending on someone else's library is an act of commitment and trust

But it is only good when:
- the piece of code is short
- you understand what you copy
- the piece of code is reliable

It happened several times that a library appealed to me just for a few methods that were handy. Depending on a library just for a few static methods I think is a shame. Why? Ok, I'll try to enumerate what a library dependency implies to me.

&rarr; Trust, when you download code which you don't own, you have to trust that the person who wrote it knew what she or he was doing. The basic functionality has to be reliable. Edge cases have to be taken care of. As a developer, you know it is not easy to do these things.

&rarr; Luck, you have to be somewhat lucky to find a library that does exactly what you need. Most of the time it will do something approaching your need and you'll have to deal with it with some wrapper and awkward code.

&rarr; Public repo publication, on the JVM I would never use a library not published on a public repo, it's just too much hassle. Most of the libraries are published though.

&rarr; Bug fixing, you really depend on the maintainer(s) for the bug fixing. The do it yourself approach is valid but you would do it only if the library is really important to you, and the library maintenance is open enough to accept pull requests. And you would have to understand the code.

&rarr; Licencing compatibility, it's low risk I have to admit, but it's better to check, we never know.

&rarr; Backward compatibility, this is the most tricky one but shouldn't influence you to go towards copying and pasting. If backward compatibility is a problem for you that means you use the library heavily, which also means that you get a lot of benefits from that library (or you should think about dropping that library altogether!). So when there is backward compatibility concerns, that means the amount of benefits outweights the bother.

&rarr; Compatibility with other libraries, always a pain but it doesn't happen that often, and generally only on large libraries. We are also in a case of benefits outweighing the disadvantages.

When you use libraries, you have to be aware of all that. And when you are an author of a library, it's even worse you have to be aware of all the users who are aware of all that. It's kind of daunting! That's what makes me think that open source libraries should be the responsibility of mainly companies, or heavily invested developers.
BUT, as the intro said, for small-ish pieces of code there is copy and paste. So much easier for everybody, users and developers. You copy that piece of code, put it in your house framework and that's it, it's yours.

I'm dreaming of a service that would help that copy-pasting practice. One might say "use a paste bin!" but I'd answer:
- you can't trust a piece of code in a paste bin
- how do you search for it?
- you don't even know if it runs

What that service of my wildest dreams would do:
- tests with 80% coverage mandatory (verifying/publishing other metrics would be nice too) -> you copy the tests alongside the production code
- live running of the tests after modification, with a green/red flag telling me if that code runs
- a limit on the number of files and lines per file (go put your library in Github if you go past that limit)
- relevant search
- double display on one screen of the tests on the left and the production code on the right (tests gives you all the things you need to know, being what it does and samples)
- cool stats like the number of people who copied a file or part of it

To summarize, that service would be a cross between a paste bin, github and an integration server.

Am I the only one here who wants that service?
