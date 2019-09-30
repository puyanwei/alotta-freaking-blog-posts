---
title: 'Makers Week Two: God of Cookery Takeaway'
description: OBSESSIVE TRAVELLING PROJECTS
date: '2017-08-14T22:25:54.020Z'
categories: []
keywords: []
slug: /@pyan/makers-week-two-god-of-cookery-takeaway-6a8b4066fe4
---

### OBSESSIVE TRAVELLING PROJECTS

So week 2 is done.

So far our projects have been making programs on London Bikes, Airports, and Oystercards. Really seems like the guy who designed them for the course really needs a holiday!

When we say programs its not the polished snazzy looking ones you have on your computer. They are things you run in a terminal with only words to show for your efforts and it they look like they have been made in 1986. I will show you down below…

Learning everyday with classmates that want to improve creates an amazing environment. There is a real sense of camaraderie in our group. With these boot camps and the industry as a whole, it feels quite likely that most people will be introverted, but our group is outgoing and has brought those to come out of their shell.

![](https://cdn-images-1.medium.com/max/800/0*zed2OXtsBUXMZWl6.jpg)

### QUALITY LEARNING, NOT QUANTITY

One of the most recent things that I have found out about myself is my style of learning. Finding a lot of examples and wanting documentation seems second nature to me. But I hadn’t thought about the quality of learning I am doing by doing this constantly.

When I do this and find an answer to what I want, am I really understanding fully what is going on? Maybe not so, and even worse because of this I may think I am.

My amazing coach is teaching me to be more thorough (which means frustratingly slower) with my learning. We have extra walkthroughs with our projects that give us more literal answers and we are encouraged not to use them, which is really difficult!

Questions to her adhere strictly to her belief of process orientated learning. This is very hard to do when providing a straight answer is easy and satisfying, but in the short run it achieves less. Asking her questions can be frustrating but I understand and appreciate this style of teaching, and am convinced that this what teaching should be.

Asking questions to her will result in the following things happening;

*   A question will be asked back, to make us think more deeply about the problem and possibly the solution.
*   The question will be reworded to make it clearer on the intent.
*   The question will be deemed irrelevant or inconsequential.
*   If it is deemed worthy of a straight answer, one will be given.

Currently I feel a bit lost, because since learning coding my process has always had a “do more exercises” mentality. This must change to a more methodical approach. It seems overwhelming as there is so much to learn.

![](https://cdn-images-1.medium.com/max/800/0*gTfxJGp_Gcocxv7Y.jpg)

My coach looks a bit like Daria, but much more upbeat and funnier!

### GOD OF COOKERY TAKEAWAY

Every weekend we are set a weekend challenge. This weekend we had to design a takeaway that has a menu, allows for selection and then sends a text to confirm the order! Its cool to have the code do a “real-life-thing”!

![](https://cdn-images-1.medium.com/max/800/0*p-kQdgd6m19W0pJi.jpg)

My takeaway is inspired by Stephan Chow’s movie God of Cookery. He is famous for making the satirical football movie “Shoalin Soccer”. In the movie he is a corrupt food critic that meets his end to his career, then becomes a monk to find his inner chef! Sounds ridiculous? Oh it is, and that’s what makes it good. Not that I’m for promoting this kinda thing but youtube might have the whole movie up there…

The food in the movie is super high quality, literally God-like standard so if you wanna buy a dish from my takeaway you’d better have a lot of dosh!

Here’s my program in action!

First we will be using the terminal to run our thing. Ruby should come with macs by default. You can type in IRB and that will open up a sandbox that you can play around with. Here I am using an alternative called [Pry](http://pryrepl.org/). It has extra features and its more colourful so its better for showing.

Once we’re in, first thing we do is require our files. This is necessary to load everything up. Once they’re “true”, we activate the program by making a new takeaway. Here we call the new takeaway, “takeaway”, but it can be any other name.

![](https://cdn-images-1.medium.com/max/800/0*xqeXz8pmXLZper6G.png)

Next thing we do is find out what other functions there are. We do this by typing takeaway.header.

Header outputs these other options. We can activate them by typing takeaway.\[function\]. Note that if we used another name other then takeaway, we would use that name dot function.

![](https://cdn-images-1.medium.com/max/800/0*I1jKZSab06S2y_M2.png)

Lets see the menu;

![](https://cdn-images-1.medium.com/max/800/0*mp-EDThZ7rSYJp6y.png)

Cheap right? The Buddha Jumping Wall is half price this week! Lets order some stuff…

![](https://cdn-images-1.medium.com/max/800/0*7zDQP-dhVKqRgk5D.png)

Notice that in the header function the choose\_dish function has brackets. We can pass arguments into those brackets and here they represent the dish number, and the quantity.

Right, lets checkout. That should be enough food.

So like the choose\_dish function, we have some arguments to pass in. These represent two codes we were given by Twilio to link them up with our program, and the third one is our phone number.

![](https://cdn-images-1.medium.com/max/800/0*xP7aDW1PeYSUVo42.png)

Here I’ve hidden my code a bit. Point being that manually having to input these codes make sure that when we upload our project to [github](https://github.com/pyan83) we don’t give all our details away there too! We could totally hard code these in and not need to have a user input.

![](https://cdn-images-1.medium.com/max/800/0*CeJqE9hyqn4rX4fZ.png)

And voila! We get a text with our order. Note the time in our message is delayed by one hour.

This project was really cool because it had this at the end which interacted with our real phones! The code for this project is [here](https://github.com/pyan83/takeaway-challenge) if you are interested, I wont explain it for now. Its pretty awesome that I’ve come this far that I can do this without much help. It was also cool seeing my fellow cohorts manage to do it too and its interesting to check out the variations we have.

Week 3 looks like its something different, moving onto making a web app this week. Should be good, I’ll keep you posted next Monday, happy codings ppl!