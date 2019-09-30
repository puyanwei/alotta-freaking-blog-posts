At my last interview, I was lacking some confidence in my Test Driven Development (TDD). This means that you write a test first to set out your intention, then test it, then it fails because the code doesn’t exist yet, then write the code and make it pass.

I have been practising this finding little puzzles via [codewars](https://www.codewars.com/). I had not touched codewars since the Makers Academy [pre-course](https://thep-log.blogspot.co.uk/2017/07/the-makers-academy-pre-course.html). Hopefully now I would be a bit more knowledgable about them now?

**MOVIE CLERK**

[The Kata](https://www.codewars.com/kata/555615a77ebc7c2c8a0000b8/train/javascript) I wanna highlight is one I did last week in [Javascript](https://hackernoon.com/tagged/javascript), and then paired with to do it in Ruby. So this should give you a nice look into comparing the two languages. I would say that I’m pretty proficient with both, but there’s always room for improvement, especially with refactoring and all that.

> Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line. Each of them has a single 100, 50 or 25 dollars bill. A ticket costs 25 dollars.

> Can Vasya sell a ticket to each person and give the change if he initially has no money and sells the tickets strictly in the order people follow in the line?

> Return YES, if Vasya can sell a ticket to each person and give the change with the bills he has at hand at that moment. Otherwise return NO.

> Examples;

> tickets(\[25, 25, 50\]) // => YES

> tickets(\[25, 100\]) // => NO

So in example 1, the first customer gives 25, then the 2nd, and the third guy gives 50 which needs 25 change, and there are two 25’s in the till. So that line can be completed so it returns YES.

In example 2, the first customer buys a ticket for 25, but then the 2nd tries to pay with a 100 bill, but there’s only one 25 in the bill so there’s not enough change so it returns NO.

![Welcome to the world of just 25, 50, and 100 notes! Sounds great to me, being a fan light wallets.](https://cdn-images-1.medium.com/max/800/0*t7cFAmIad35XU5U0.jpg)
Welcome to the world of just 25, 50, and 100 notes! Sounds great to me, being a fan light wallets.

**STEPS (IN JAVASCRIPT)**

The first thing to do is to break down the problem into smaller bitesize chunks so its easier to understand. Here’s the steps I kinda outlined in my planning;

1.  We need to go through each number of the array (customer), and work out if it can give change or not.
2.  If at any point of the queue any customer cannot get change return NO.
3.  If they can get change, we must update the till depending on what note is given;

*   25 note gets no change.
*   50 note gets 25 change.
*   100 note gets 75 change, which is one 50 and one 25 or three 25 notes.

1.  If all is well, and everyone gets the correct change, then return YES.

I though a hash data structure would be best for this. This would be used to update the numbers of notes in the till;

![](https://cdn-images-1.medium.com/max/800/0*lOKfXozhpbzXlHfs.png)

Hashes work in key/value pairs separated by colons. So here the keys are 25, 50, and 100, and the values are zero. There are zero notes of each when a new bunch of customers line up.

Now we wanna make checks for if we can give change;

![](https://cdn-images-1.medium.com/max/800/0*h0mEHMZBbKkFE_oH.png)

Here is a function canMakeChange where you input 25, 50, or 100 and it looks at the till to see if it can make change.

For 25, there no change needed so its always true.

For 50, it needs 25 change always. Here “till\[25\]” is looking for the key pair of the 25 in the hash, and asking whether that number is above zero. If it is, there is change for a 50. We can edit the hash ourselves and run the [code](https://hackernoon.com/tagged/code) to test whether this works. But in doing this process, I had written tests.

For 100, its a bit more complicated as there are two possible ways of giving change. You can give one 50 and one 25 or three 25 notes for 75 change. In the same way as before, it looks for various combinations of these notes in the hash till and returns true. In the code I have extracted it to another section so that its more readable. It is saying, if note inputted is 100, return true if the till has more then three 25s, OR (the two pipe symbols “||”) more then one 25 AND (the double ampersand “&&”) more then one 50 note.

Ok, so lets make our till update if change can be given, and it does. Our till will have money going in, and money going out back to the customer.

![](https://cdn-images-1.medium.com/max/800/0*G6iLaytTyD2E9_1p.png)

So this function accepts an input number, and then updates the hash till. Note that ++ and — means adding or subtracting one to itself. This is such a common thing that Javascript has created this shortcut.

With 25, it adds 1 to the 25 hash. Meaning the till should be “hash = { 25:1, 50:0, 100:0 } if the till is empty before this input. Since there’s no change, no need to deduct any of the other notes.

With 50, it subtracts one 25 note, but adds another 50 note to the till.

With the 100 note, again its more complicated. We need to find out if the till has one 50 note and one 25 note, or three 25 notes. So here, we use the other functions we had created before to check it this is true and then update it appropriately. With one of each, we subtract a 25 and a 50 and add in a 100. With three 25s, we deduct three 25s only.

Finally, we link everything together in a more controller type function. This is when a function is used as more of a place which calls other functions, rather then us calling them separately.

![](https://cdn-images-1.medium.com/max/800/0*s4842Abl04kXj_si.png)

Here, we use a loop which goes through our list and applies it to each individual element, ie each customer’s payment. Var i = 0 is telling it to start the loop at the first element of the array, i < array.length tells it to stop looping at the end of the list and i++ is telling it to go through elements (represented by array\[i\]) of the list one by one.

For each cycle, it we input the element into our canMakeChange function and if it is true, then giveChange and update the till. With if statements, if we are asking if something is true, we don’t have to explicitly state it. For example, if(true ===true) can be written out as just if(true).

If it cannot make change, then return NO. If it manages to complete the loop with all the change given return YES. Once we return something in Javascript, it breaks out of the function meaning that the code stops there if there is anymore.

![Some tests to practice my TDD and also keep an eye on my code working](https://cdn-images-1.medium.com/max/800/0*Gq9F-M2Zuhl3LqKG.png)
Some tests to practice my TDD and also keep an eye on my code working

**READABLE RUBY**

Here is the comparisons between Ruby and Javascript. Here we call the function sell to initiate it.

![Javascript Version](https://cdn-images-1.medium.com/max/800/0*8lcv-8H8MkcD2ziB.png)
Javascript Version![Ruby Version, with case conditional](https://cdn-images-1.medium.com/max/800/0*L-o_docckjd1Cgam.png)
Ruby Version, with case conditional

I really like the code in Ruby, it seems so much more readable. There are some really nice things like; functions with question marks returns true or false, loops are shorter, and the last lines are explicitly returned, it reads very nicely like it reveals its intention of what its trying to do.

There are also a lot of in built functions in Ruby which shortcuts a lot of common tasks. For example \[string\].reverse will reverse a string (duuh) but in Javascript you have to manually write the way of doing it, which means more lines of code.

A lot of the problems I had with writing the Javascript code involved remembering that all the functions needed to return something, since if you don’t do it just doesn’t know what to do and you get an unexpected undefined outcome!

I also tried to use a forEach loop in Javascript before finding out you couldn’t break out of it when a condition was met. Javascript also has an inordinate amount of brackets and curly brackets all over the place, which increases the chances of typos.

That being said, I have been mainly focusing on Javascript a lot. I find that it is quite flexible to use with the web, you literally can write some code in your HTML file, or even try some out in the sandbox console if you Alt + Apple + I it!

![Going to View/Developer/Developer Tools in Chrome (or Alt + Apple + I) opens the console where you can play around with Javascript](https://cdn-images-1.medium.com/max/800/0*muUt4wmpUHuntBce.png)
Going to View/Developer/Developer Tools in Chrome (or Alt + Apple + I) opens the console where you can play around with Javascript

It has been an interesting challenge trying to explain things like this in the most simplest form, hopefully that all makes sense! The code could be refactored (edited) to make it better, but for now I’ll leave that to another post. I’m sure many expert readers can see some inefficiencies and (gulp) some mistakes? Hopefully not.

I dunno how many of you non coders will be able to understand this but I tried my best…

Github version [here](https://github.com/puyanwei/ticket-clerk).

**ITS DEFINITELY PERSONAL, BUT STILL BUSINESS**

The job-hunt as been real. The rejections have been tough. But through each interview I learn more, more about myself and more about the process.

Throughout Makers I’ve been hearing things from two camps, the “Get \[Almost\] Any Job” camp where after you get one year’s experience your super employable, and the “Go For The Jobs You Really Want” camp.

In the end I think it kinda of depends on the person, and their goals. People have different aims and personalities, some are able to grind out any job for a while, where as others really need to feel the love for where they work.

Its rough as I feel I’ve put my all into this process and yet still come up short. There’s no doubt that I’ve been making mistakes in my interviews, namely saying stupid shit due to being nervous or whatever.

Its becoming clearer to me that impressions count for a lot. If they like you, and see the potential that they can get along with you in a team, then almost other things don’t matter as much. I hate that phrase, “Its not personal, its business”, which implies that business and personality are separate things. It couldn’t be further from the truth, business is all about who you get along with, the networks you create, the deals that you do.

Maybe this is a phrase commonly used during firings, especially when a company needs to do some cutbacks. But even then, it couldn’t be more personal, certain workers are preferred over others.

Anyways, gonna keep trying. Its hard when so many others get jobs and you try to not instinctively compare.

![How many kids thought this could be their dream job? :D](https://cdn-images-1.medium.com/max/800/0*0AYBdGJTFipCrJpd.gif)
How many kids thought this could be their dream job? :D