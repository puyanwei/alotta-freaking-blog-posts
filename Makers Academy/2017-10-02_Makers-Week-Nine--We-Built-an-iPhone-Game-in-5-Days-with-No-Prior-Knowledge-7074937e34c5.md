---
title: 'Makers Week Nine: We Built an iPhone Game in 5 Days with No Prior Knowledge'
description: >-
  This is a long ass post, so if TL; DR scroll to the bottom, check out the gif
  of our game.
date: '2017-10-02T23:34:25.486Z'
categories: []
keywords: []
slug: >-
  /@pyan/makers-week-nine-we-built-an-iphone-game-in-5-days-with-no-prior-knowledge-7074937e34c5
---

This is a long ass post, so if TL; DR scroll to the bottom, check out the gif of our game.

Last week it was our mini mock final project. We came up with a bunch of ideas, rounded them down and then got given our our groups, and then within it we picked one of them to do;

### P-YAN AN IDEAS MAN?

I’ve always prided myself on being an ideas guy. Its the execution i’m lacking in. So when the time came for us to submit our ideas I kinda felt that I should be able to get one through. Each student picked 3 and then they got rounded down.

![](https://cdn-images-1.medium.com/max/800/0*qzekDt2AKjAEmAM0.jpg)

“DING!”

My ‘strategy’ was to pick something that was general enough to be open, but also have a specific thing in mind that could be cool. I think good ideas at this stage can be broken down by answering the following questions;

*   Is there a particular thing you’d like to try out and explore?
*   At the end of it, is it possible to have something tangible to show for it?

Two outta three of my ideas got picked to the final choices, and our group unanimously agreed that we wanted to make a iPhone game. Here’s my ideas anyways, with those criteria in mind;

1.  **iPhone game using the tilting motion** — We wanted to try out making a phone app, and a game and use the gyrometer feature. And we’d have a cool app on our phone to show for it afterwards.
2.  **Chrome extension which funks up the pages 80s style** — Could be cool to try and make a Chrome extension plugin. The Chrome extension could branch out into any other idea. At the end of it you could have something that you could share with others and let them download and install it to see for themselves what it does.
3.  **Machine learning pathfinder for London Underground** — My weakest idea tbh, as I had already [seen it done before](https://www.youtube.com/watch?v=aKYlikFAV4k), but thought it could be a cool thing to expand upon. But machine learning is a hot topic these days, but this idea for sure doesn’t seem to have the accessibility or fun of the other two.

### WHERE 2 START

Starting out projects like this always seems pretty overwhelming at the beginning. The important thing is to identify what needs to be done and plan for the future;

**Make a Plan!** — Super important to get things going. What programs are we going to use? What is our testing framework? The first aim is to get a MVP completed, ie a Minimum Viable Product. For us, this would be a ball on the screen that would move around due to tilting the phone.

![](https://cdn-images-1.medium.com/max/800/0*Mmwo0em5d1qLs5V5.jpg)

Original planning page from Day 1

Ironically, Swift was chosen by our group in no time at all. It was either that or React Native, and with our coach’s advice that’s what we went with.

**Setup The Environment** — We want to get our [Github](https://github.com/pyan83/pokeball) repository setup, download all the relevant softwares and set it up ready to be used. This can take a lot longer then anticipated especially when working with stuff that we’ve never used before.

![](https://cdn-images-1.medium.com/max/800/0*CNkX0OXXwFGtKqJ_.png)

The super intimidating user interface of XCode!

**Agile Setups** — Set up a plan of when to do morning stand ups and end of day retros. These are plans for the day and end of day evaluations. These are super useful to keep things in perspective and take a step back to remind ourselves what we’re doing. Direction can be easily lost sometimes when members are super immersed in their work.

![](https://cdn-images-1.medium.com/max/800/0*Dm1U-GfEP1OYGjpL.jpg)

Day 2 Retrospective — The Good, The Bad, and the Confused?

Setting up XCode is a pain in the ass. You have to go to the Apple Developer page, sort out sign ins, and fill out forms. Once done with those, you have to do more downloads and then select an extra option on your phone to activate it once it downloads.

For some reason, my developer account had issues where it’d never save my sign in, so I’d have to do it like every time! Super annoying…

![](https://cdn-images-1.medium.com/max/800/0*dUhOOQtmTiuBTyht.png)

Bane of my existence this week

On day 2 we made an executive decision to switch from Swift 3 to Swift 4. Swift 4 had just been released the week before, so we thought it would be better to work with Swift 3 because there’d be more documentation on it.

However, after a few of us realising that our newly updated OS11 iPhones weren’t compatible with Swift 3, we decided to go for Swift 4. Another incentive was also the fact that after this project, if we decided to try out more apps we would have to learn Swift 4 anyways, so its more beneficial.

End of day 2 we managed to finish our MVP. We found a good spaceship tutorial which used the gyroscope movement and adapted that code into ours. We found a Pokeball sprite that we could use, and so that was the beginning of our Pokemon themed game…

![](https://cdn-images-1.medium.com/max/800/0*cnivOaLecOKvk0Vc.jpg)

### XCODE TESTING IS AWFUL

From my limited experience of checking out maybe five(?) testing frameworks, XCode’s XCTest was by far the worst.

*   **Interface** — XCode is pretty UI intensive, meaning that you have to use their software to do everything. I found it pretty overwhelming, as they had gone completely nuts with the amount of options for everything. I’m not talking options for properties of things that you create, but the actual user interface itself! This means its not intuitive at all and just finding the tests themselves was confusing enough, let along knowing how to run them!

![](https://cdn-images-1.medium.com/max/800/0*nLYQH7UCKkKcmyb9.png)

The tiny diamond button shows your tests! Hovering mouse over test icons reveals play button to run your tests!

*   **Speed** — Every time you ran a test, XCode built the app. This meant every time you ran a test it would take at least 20 seconds, which is just insane if you compare it to the instant results you get from other testing frameworks.
*   **Visibility **— We did not realise there was a console that outputted messages until day 3! The console was also quite random too, sometimes displaying a message when there was an error, and other times not showing anything. We never understood this in the end.
*   **Testing Games is Hard — **Since the other groups also did games, this became a common theme in the groups. Most groups worked with looping frames to get the animations to interact, and so once their game started, you cannot simulate what is going on within a controlled environment. This is especially true because most games have a ton of randomness in them.
*   **Testing Tilt Motion is Hardest — **So super how do you test tilting a phone motion? XCode has a simulator phone that you can use, but after some research it was discovered that simulating the tilt on your computer is just not possible.

![](https://cdn-images-1.medium.com/max/800/0*1lfoZ2ZwBdjXAZD2.png)

#fml

*   **Record Button Saved the Day **— We found a record button on day 4 lol, and that wrote down in the code what was being pressed etc. This was great because it finally gave us some insight into what the objects were called for the testing framework. With this feature, we managed to pull off some tests finding elements in our game.

### SMALL THINGS COUNT

Looking back at the [Acebook week](https://thep-log.blogspot.co.uk/2017/09/makes-week-eight-acebook-home-stretch.html), I think we learned a lot from it actually. Adding in smaller features at a time and refactoring the code was super helpful, especially for splitting up the work between different people in the group.

When adding the enemy Team Rocket, in typical fashion they caused complete mayhem. For some reason when they appeared on top of our border, the game would instantly be over and we just couldn’t work out why.

![](https://cdn-images-1.medium.com/max/800/0*if1bpaNzObutziil.jpg)

Typical Team Rocket causing tons of trouble for us!

So as a purely coincidental decision nothing to do with that at all, we decided to get rid of the borders and make it an Astroids style thing where if you go left off the screen you would appear on the right, and vice versa for up and down. This actually made the game more fun!

![](https://cdn-images-1.medium.com/max/800/1*rd55MaE9pCCyMYe7yhVAsQ.gif)

Outtakes showing our bugs!

I looked at previous presentations and wrote a rough outline for the group to participate in. Structures are basically the same, so it was pretty easy to prepare.

I had also overheard that doing live tech demos are basically banned for final projects, they’re **_always_** videos, as too many times things have gone wrong. So I insisted that we include a video.

It was also kinda weird to think about how one would go about presenting a game which involved tilting. Showing a screenshot of the game (great timing for that new feature, Apple) would be good, but it wouldn’t show the physical tilting of the phone.

I kinda thought about having a split screen and after some quick googling I realised it was pretty easy to do in iMovie. Just needed to synch things up and it’d be great. It worked like a charm…

![](https://cdn-images-1.medium.com/max/800/1*Uh_QZlclJtTjOVmi4EVixg.gif)

Its POKEBALL RUN! Coming to the App Store soon!

Our presentation went really well, and we achieved so much within 5 days. This was one of my favourite projects so far. I hope that with the final project it will be similar in trying something new and interesting.

Check out the [Github Repo](https://github.com/pyan83/pokeball), there are instructions to play the game yourself but be warned you will have to go through all the Apple Developer stuff, as well as downloading XCode etc!