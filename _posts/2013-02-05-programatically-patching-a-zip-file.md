---
layout: post
category: code
---
{% include JB/setup %}

There is no good excuse to patch continuously the result of a build. If you have to patch a build more than once, this means you have to change your build somehow and take that patch into account in your normal build. You have to normalise your build.

Now reality. Reality is terrible because it makes following principles really difficult. Luckily reality doesn't happen too often, but when it happens it's good to be able to repeatedly patch a zip file.

That's when I tried to find a programatical way (on the JVM) to access a file burried in several layers of zipped packages (zip in a zip in a zip). I thought I needed to do that only once, so I went the ad hoc way (quick and dirty). I used Groovy at first, as it helped me before for this kind of scripts. I realised quickly though that the main tool I had to help me was just the standard java.util.zip API. I could have used third libraries as well. But none was making easy digging into several layers of zip files in a streaming fashion. Because ear packages can be very large, you don't want to extract everything in some folder, do your business, and then re-package everything, this would be inefficient from a processing and memory point of view. What you want to do is handling a continuous input stream that you would use to create an output stream, transformed when relevant.

So there I went, I wrote that code for my specific file I had to patch, but the resulting code turned out to be very ugly and not readable. This was a mistake. So I wrote a generic recursive version that would do the same, and it turned out to be a much cleaner, shorter and readable piece of code. In the meantime I dropped Groovy for Java as I needed that code to be as fast and efficient as possible. And then I dropped Java for Scala as I wanted that code to be less boilerplaty. And finally I though I spent way too much time on that small piece of code to not share it. 

And that's when I thought that [Copy and paste can be relevant](http://matthieus.github.com/ideas/2013/02/04/copy-and-paste-can-be-relevant/).

For the record the zip patching code is below (and you can check the tests in the [testedGists](https://github.com/matthieus/testedGists) repo):
<script src="http://gist-it.appspot.com/github/matthieus/testedGists/raw/master/src/main/scala/testedGists/TransformFileInZip.scala">
</script>
