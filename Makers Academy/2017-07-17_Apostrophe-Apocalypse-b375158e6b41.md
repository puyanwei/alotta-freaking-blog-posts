---
title: Apostrophe Apocalypse
description: 'Hi dudes,'
date: '2017-07-17T11:12:15.541Z'
categories: []
keywords: []
slug: /@pyan/apostrophe-apocalypse-b375158e6b41
---

Hi dudes,

So week 2 of the Makers Academy pre-course comes to an end, and I have to say that it has been challenging. The week involved watching some [Ruby Kickstart](https://vimeo.com/channels/844657) lectures, then completing the 37 exercises.

Not only do they get harder, but each exercise has an auto test feature which checks our answers, and some of them will test extra things such as throwing in some blank spaces, symbols and negative numbers.

Solutions are there, but it seems rather unsatisfying to just copy them down. The ones that I did complete were not very similar to the answers, but I think its ok if it passed the test, since I’m learning that a lot of the time there will be multiple solutions to these problems.

However the process one has to go through takes an incredibly long time in this initial stage. Googling and finding existing examples and forum posts, Stack Overflow is nothing but our bible!

It is a balance between having a go at solving the problem and then moving on. It was suggested to spend 45 mins max on each exercise, but I clearly didn’t do that and ended up banging my head against the wall. I’m sure that 90% of the challenges would not been completed by me with that timeframe.

![You would think their design should include a proper apostrophe wouldn’t you?](https://cdn-images-1.medium.com/max/800/1*pjmBS9r0NAqrcuWLnouvlQ.jpeg)
You would think their design should include a proper apostrophe wouldn’t you?

The infamous challenge 2:7 gave me some crazy troubles! The question was to make a method that would output every other word. Do not include special characters apart from apostrophes.

Previous exercises helped here. I started out by using regular expressions to substitute out those special characters by saying only include A-Z, a-z, and ‘.

Then split up the sentence into an array, then use a for each loop to iterate through it and only return it if its in an even position.

That took me like an hour or so. Seemed good in my own testing in IRB. Submit, failed all but one test.

```
alternate_words("don’t hello don't yes") #=> "don't dont"
```

Can you guys see it? The answer is right there. I would suggest you get your glasses. Maybe a magnifying glass whilst your at it.

If you got it then grats! The answer is that apostrophes have two different types, a curly one and a straight one. On a Mac to use the straight one its very easy just a simple uncomplicated **shift + option + \]** will get you this super common apostrophe (sarcasm loses its quality in text form, damn).

[Stack Overflow](https://stackoverflow.com/questions/45111600/keeping-a-single-quotation-mark-in-regular-expression-ignored) my savior! Well now you know. I will never look at apostrophes the same way again…

Either way, its all good. Enjoying the process even though it is stressful. I will always go back to reading Daniel Pink’s book “[Drive](https://www.amazon.co.uk/Drive-Daniel-H-Pink/dp/184767769X/ref=sr_1_1?ie=UTF8&qid=1500289707&sr=8-1&keywords=drive)” talking about how people are much happier in mastering something if they enjoy the process rather then the outcome.