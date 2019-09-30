---
title: I wrote a CodeWars Puzzle and it was a disappointing experience
description: What is Codewars?
date: '2018-09-02T10:40:39.433Z'
categories: []
keywords: []
slug: >-
  /@pyan/i-wrote-a-codewars-puzzle-and-it-was-a-disappointing-experience-d0126d5c1c76
---

### What is Codewars?

[Codewars](https://hackernoon.com/tagged/codewars) is a place where you can solve coding puzzles and then feel pretty smug about it. The smugness is then recorded in points that level you up on the site. You do all the puzzles within their site and try to pass its tests.

Maybe the creators are obsessed with martial arts because that’s how everything is themed. Katas are like the level of difficulty except that lowest is best and highest is newbie status which is level 8.

![Codewars is themed towards Martial Arts which is pretty fun!](https://cdn-images-1.medium.com/max/800/0*j5bkrk41xMeWfP25)
Codewars is themed towards Martial Arts which is pretty fun!

In all fairness it is quite fun, although sometimes the puzzles are not that clear and/or you don’t know what the tests are testing when it comes to edge cases which can be quite frustrating.

A good tip is to check out the discussions if your stuck because some of the puzzles may have some inconsistencies or be unclear about certain things. Cant see the discussion button? Yeah you need to make sure your window is a larger size, as for some crazy weird reason that button disappears.

![](https://cdn-images-1.medium.com/max/400/1*IjTe-csZmXrmlimuhvIVgA.png)
![](https://cdn-images-1.medium.com/max/400/1*F11EBGDF7d9DWJipvyynxw.png)
![Breakpoints still has bugs when I noticed this last year. Left is full screen, middle and right are slightly thinner widths. Losing the discuss button is huge as its important to find out if the puzzle has inconsistencies that other users report](https://cdn-images-1.medium.com/max/400/1*jBbWOVNaBI-DtzYyFXFbsQ.png)
Breakpoints still has bugs when I noticed this last year. Left is full screen, middle and right are slightly thinner widths. Losing the discuss button is huge as its important to find out if the puzzle has inconsistencies that other users report

### Pre-course Pre-face

Actually the idea of doing this had been on my mind for a while now. Before we started the coding boot camp, we were asked to use Codewars to practice what we learned.

Then afterwards, we went back to it with our new found confidence… still realised that it wasn’t that easy, but used them to practice for tech tests that interviewers might set. I remember using them mainly to find some puzzles to practice testing first on (TDD).

![Old blog posts reveal my struggles doing codewar puzzles](https://cdn-images-1.medium.com/max/800/1*eSVYiRodGSJGOjGlXsJAoA.png)
Old blog posts reveal my struggles doing codewar puzzles

So I’ve always thought, well its been a year since doing the pre-course and it’d be kinda a cool milestone, so why not give it a go and see what its like?

### The Puzzle!

I’m a huge Hearthstone fan, and thought that there could be potential continuing this theme later on if this became successful.

My idea was to make a puzzle based on the mechanics of the game. In Hearthstone, you put minions on the board and try to make them trade with each other in the most efficient way.

![Here my minions are (\[2, 1\], \[2, 1\], \[2, 1\]), my opponent’s are (\[1, 4\]). When I trade my 2, 1 into his 1, 4 the result is that my 2, 1 dies because it has one health and the 1, 4 has one attack, and the 1, 4 ends up being a 1, 2 because it 2 from the 2, 1’s attack is deducted from the 4. This was not a good trade for me!](https://cdn-images-1.medium.com/max/1200/1*5jYJmjvlk4EZfgx5w__tRQ.png)
Here my minions are (\[2, 1\], \[2, 1\], \[2, 1\]), my opponent’s are (\[1, 4\]). When I trade my 2, 1 into his 1, 4 the result is that my 2, 1 dies because it has one health and the 1, 4 has one attack, and the 1, 4 ends up being a 1, 2 because it 2 from the 2, 1’s attack is deducted from the 4. This was not a good trade for me!

Each minion has an attack and health value. The attack value never changes, and when two minions trade, their attack values deduct their health values. If either minion ends up with no health they die and are removed from the board.

Choosing to convert this into a coding problem was interesting, but I already had an idea of the input and output I wanted.

### And it’s live!

After a little while I decided to post it live. It did take a while to work out how to use their platform to write the code, the tests and fulfil their criteria. It is quite hard knowing what kata to put this at, and at codewars I have noticed that the levels system does seem rather inconsistent because different people find different puzzle hard, it can be relative…

I found their documentation rather unclear on a lot of things, it seems that trial and error ended up being the best way of understanding how things worked, which mean posting and reposting multiple times.

![](https://cdn-images-1.medium.com/max/600/1*JesQ1vrXEXh6MS5iT-Q4iQ.png)
![All tabs had to be filled in, Complete solution, Initial Solution, Test cases, and Example Test cases.](https://cdn-images-1.medium.com/max/600/1*nCGacueZUgPD5bnbNLZp_Q.png)
All tabs had to be filled in, Complete solution, Initial Solution, Test cases, and Example Test cases.

Once it was live I looked forward to the variety of answers that people would come up with. There were a few that I thought were interesting, manipulating the order of the stats first to make it easier for the trade calculations.

Its clear that there are some veterans in the game want to get on the overall leaderboard by jumping on the new katas that are created, I assume they have already done most of the existing puzzles on the site.

This was because I quickly got feedback about my kata, which was great and I used it to clarify my description. However soon I got feedback about not having random tests which I had no idea what was about. I already wrote 31 tests and looking at their documentation there was nothing written about it.

Apparently random tests is meant to be implemented to stop people from cheating by manipulating the tests to pass. I think its quite bad for the platform to make everyone do random tests for their puzzles when;

1.  Their documentation says nothing about it.
2.  They make everyone do it even though it seems to be an edge case and I cant imagine that there are many cheaters out there because it is a lot of effort.
3.  Surely it is easier to keep track of the cheaters due to their high scores achieved in quick time, and automate that instead?

### And its dead… — D: ←(Annoyed Face)

I thought it would be a good idea to let community members to contribute and edit my kata, and so one guy added the random test into my tests which was nice. However, his test was slightly wrong and therefore correct answers started failing and since I didn’t really understand what he did I think my puzzle got downvoted and around a day later it was automatically retired

When I was a newbie and first started doing these, it was interesting to see the solutions that were voted up for as being ‘clever’ or ‘best practice’. Eventually I concluded that ‘least number of characters’ = best solution! Now I know that actually that is awful and it really should be ‘most readable’ or ‘easiest to understand’.

![What are we saying to new coders when solutions like this are being voted as ‘clever’? Note, changed slightly so this wont work. How readable does this code seem to you?](https://cdn-images-1.medium.com/max/800/1*IC1QKmmu0fSK1V4ZP3gRFA.png)
What are we saying to new coders when solutions like this are being voted as ‘clever’? Note, changed slightly so this wont work. How readable does this code seem to you?

This is one of the problems of codewars, and I’ve seen much feedback from other users that complain about this and would like to see another category created for this. Having the shortest solutions been voted for as ‘best’ gives out mixed messages to what is great code.

### **Broken Windows**

In freakonomics there is a theory called ‘Broken Window’ theory. It talks about how a building has a broken window, and after time graffiti shows up and the area gets much worse. The inclination is that no one has fixed the broken window, and therefore no one cares about this building/area.

![No updates to the main site for over a year??](https://cdn-images-1.medium.com/max/800/1*nZt95klvBUJy-HTOItYD0Q.png)
No updates to the main site for over a year??

With the lack of communication from any ‘staff’ and the no recent improvements to the site, it really feels that this is a place that just isn’t maintained or cared for anymore. It had a broken window and now more things are breaking around it.

Any help seems to only come from community members, and having [automation](https://hackernoon.com/tagged/automation) with no feedback feels terrible when trying to solve issues… aka ‘YouTube style’

![Today Codewar’s front page for a new user doesn’t even seem to be live anymore?](https://cdn-images-1.medium.com/max/800/1*Gts8iaWTXFXcF0yYSFoaGw.png)
Today Codewar’s front page for a new user doesn’t even seem to be live anymore?

This can be understandable considering looking at their github there are two contributors and only one of them is a dev. The whole site is maintained by one person and that doesn’t seem to be his main priority (they have another website qualified.io).

Having users be able to create katas easily through great support and documentation would give the site more credibility rather then frustration. My experience was not great at all, my puzzle went live for as long as it took for me to write it up, I got complaints about random tests which is not mentioned at all in the documentation and then an automated retirement of my puzzle was implemented.

There was no communication was fed back to me as officially why, and how it could be reversed. Having other users suggest to ‘keep submitting more and cross your fingers’ is a terrible infrastructure and totally unmotivational.

![No response at all, their twitter seems to have died the last activity was in April](https://cdn-images-1.medium.com/max/800/1*LwpsWYsAfAGDvFwji-jLsA.png)
No response at all, their twitter seems to have died the last activity was in April

### Final Thoughts

All in all though, for practicing coding it is pretty good training, just keep in mind that readability should be priority and use the site’s filter and comments section to find good puzzles because some can be unclear and have edge cases which will not allow you to pass the tests.

As for creating katas I would say it might not be the best. It takes a lot of effort and then you have to hope that the automation accepts it, so it may take a few attempts before one gets accepted, and who has time for that?

The original puzzle on [codewars](https://www.codewars.com/kata/5b6598839756804e5c00005a) is here, but as an alternative I’ve created my own repo of my puzzle if you guys wanna have a go at it, feel free to fork it [here](https://github.com/puyanwei/hearthstone-trading-minions) and get the tests passing!

Have a great week and happy codings!