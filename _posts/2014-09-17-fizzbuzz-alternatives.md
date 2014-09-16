---
layout: post
title:  4 alternatives to the Fizzbuzz test for hiring programmers
date:   2014-09-17
categories: developers hiring
---

I compiled a list over the last 100 so-called programmers who came to me
looking for a job. 75 of them failed one or more of our three
simple programming tests. Let me emphase that, 75 out of 100 applicants to a
programming job can not program. At all.

You might have heard of the Fizz Buzz test. I first read about it on Jeff Atwood's
[excellent blog](http://blog.codinghorror.com/why-cant-programmers-program/).

_Write a program that prints the numbers from 1 to 100. But for multiples of three print "Fizz" instead of the number and for the multiples of five print "Buzz". For numbers which are multiples of both three and five print "FizzBuzz"._

About 7 of 10 made this test, but when we took them to step two many of the
programmers still could not program at all. It seems like they have read about
the fizz buzz test in blogs and just repeated a solution they'd read about before
the interview.

So we needed something else. We started by replacing 'FizzBuzz' with a different
word, and saw that more people failed. Remember, the goal is not to make people
fail on tests - only to quickly discard the people who can not write software
at an early stage to save time and effort for both of us.

We introduced the following tests to the applicants.

## 1. Anagram

_Write a function that takes two words as an argument and returns true if they
are anagrams (contain the exact same letters) and false otherwise._

Sometimes people don't know what an anagram is. That is not important so we
explain it to the applicant. The interesting part is to see if they solve it at
all - and if they solve it in a smart way. The smartest developers almost always
resort to first check the length of the words and return false directly if they
are not exactly the same length. Then they sort the letters in the words
alphabetically and compare the strings equality.
Some people stress out over the problem and create arrays and iterate over them,
keeping track of which ones are in the other words. It works, and if they are
on this path they usually can write software too. The ones who shake their head
and can not think of a single thing to do with the words - they seldom make it
to the next interview.

## 2. Taxes

_Write a function that takes two arguments, an amount in dollars and a tax percentage.
Return an array with the tax amount in cents._

I _want_ the applicant to comment on why the hell we are asking him or her to
return the value in an array. Otherwise, the math involved is simple enough
for any programmer to know it by heart. If they start to talk about things like
_"I am a programmer, not a math student"_ don't fall for it. This is basic math
and math is an important part of programming.

## 3. Bug fixes

_There are three big obvious errors in the code below. Which ones?_

{% highlight ruby %}
def fix_spelling(name)
  if(name = 'twittr')
    name = 'twitter'
  else
    fix_spelling(name)
  end
  return 'name'
end
{% endhighlight %}

There are actually more than three errors in this code, and it's usefulness can
certainly be discussed. I want the applicant to at least mention that we should
be using == instead of = since the if statement will always return true. I also
want them to notice that we are returning 'name' no matter what, and that we
have a potential eternal recursion going on here.

## 4. Box size

_Write a function that takes three measurements in centimeters as input and returns
a the volume over a litre_

Americans may need to google how much a centimeter and a litre is, but otherwise
this should be an easy task for most programmers. Things I want to hear the
applicant ask is _"Hmm .. what should we do if the volume is less than a litre?
Return 0 or a negative number?".


## Conclusion

This is some of the test that I use when I hire people over at [Standout](http://standout.se/)
and as of right now we use [Devb.io](http://devb.io) to find new applicants
to our jobs (skipping the high hiring fees).

I again want to emphasize that this is only to sort out the real developers
from the crowd. I really don't want to waste anyone's time and energy on doing
multiple interviews when we both can find out with a simple test that they're not
going to make it. No pointing fingers, no harsh comments - just a simple test
to find who we are looking for.
