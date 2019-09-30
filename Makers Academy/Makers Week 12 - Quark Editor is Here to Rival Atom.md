Sorry for the lateness of this post, I chose Mondays as a good time to write them because its almost guaranteed that it wont be as busy. However yesterday I was doing my applications for Makers Careers Fair jobs and the deadline was today.

### REACHING THE MVP

When starting a big project like this, we have been taught that the best approach is to make an MVP and use that as your first stepping stone. A Minimum Viable Product is the most bare bones minimal amount of your product that you can do. So for us, creating a text editor, it would be have something where we can write text on.

Things were not as simple as it seemed because we needed to test first, and we had no idea what we were meant to use for testing, let along how it works and how the syntax was written.

The Electron documentation said that Spectron was the official testing framework, so we tried to use that. However it was quite difficult in finding the elements on our page. The typical “document.getElementId()” which did exactly that didn’t seem to work, because our app did not call them documents, it was called something else.

Once we did figure it out, it was Wednesday (we aimed to get it done by Tuesday), and there was high fives all round and a huge sigh of relief.

![](https://cdn-images-1.medium.com/max/800/0*GDtTGT50xmj_Oc9i.gif)

What testing with Spectron looks like!

### CRUD & LS

After that, we realised that we would have to include some CRUD functionality. CRUD is another technical acronym that basically stands for “Create, Read, Update, Delete”. It is a way of explaining the most common basic functionalities of all programs.

Including CRUD was difficult, as it was part of Node JS but again like many other things, we had never used it before. We would be using a module within Node called “LS” that let us move and work with files and directories.

We managed to incorporate a folder tree as well on the side. This was done by having LS look at our current directory, loop through it and put it in a list.

An interesting feature of Electron is that it doesn’t have copy/paste shortcuts unless you explicitly add it in. This made is quite difficult to try and debug our problems as without it made it much longer to type in everything to check our app!

It was quite unclear as to how or where to incorporate it into our app. When it came to testing, it was rather problematic because Spectron did not seem to have the ability to click on prompt boxes when you wanted to imitate a save or load.

### THE CURSED CURSOR

Probably the most time spent on anything was trying to get our cursor to behave the way we wanted it. There became deja-vu type memorise of the dreaded [apostrophe](https://medium.com/@pyan/apostrophe-apocalypse-b375158e6b41) again, but to this that was nothing in comparison.

The bane of our existence, for this project!

What was happening was that on every keystroke we applied [Prism.js](http://prismjs.com/), which was our syntax code highlighter. This library looked at the text, and through looking at the various patterns it would be able to recognise which coding language was being written.

However, everytime we ran this program and then told the cursor to go back to the editor afterwards, it would always return back to the top left. This meant that it would always end up typing backwards!

![](https://cdn-images-1.medium.com/max/800/0*LfsxMVs-F3Mb9UsM.gif)

We probably spent over a third of our time trying to figure a workaround to this problem. The worst case scenario would be that we would just have button on the page that you could click instead.

On Day 8 (its a 10 day project!), we got a breakthrough and got it to work! We had to have code to keep track of the cursor’s position, then when it got reset move it back to where it was. Its quite amazing to see the final product how it looks like nothing is happening! But so much blood, sweat and tears went into solving this bug!

![](https://cdn-images-1.medium.com/max/800/0*TprElgzUYgPv8kJ5.png)

We used Trello to help us organise our project. That syntax bug on the todo list for so long!

### FINAL PRESENTATION

It was really amazing to see how we managed to pull things through last minute. I mean, we were super last minute! The demo video was shot like 2 hours before the final presentation, we had to fix a lot of bugs the night before, so shooting the video became very late.

I felt bad for my colleague, who was in charge of presenting the demo because he had nothing to work with which made it difficult to practice. We probably did about 10 different recordings before we were happy and then I had to edit it on iMovie and upload it to slides.com.

For a 90 second clip, for no apparent reason apart from being totally trolled, iMovie seemed to want to take like 20 minutes to render the clip!

The presentation went really well, it was great to not only see our group do so well, but the whole cohort step up with their projects too! Its quite strange to finally have our own final project be shown, since I’ve been to about four graduations, but I’m honoured to have been a part of this, and also be the last cohort to only have one coach.

Here are the projects from Blue-July Cohort 2017!

**QUARK TEXT EDITOR** **— **A much, much smaller version of Atom (get it?), text editor for writing code. Built using Electron, which is HTML, CSS and Node JS.

![](https://cdn-images-1.medium.com/max/800/1*-5UsA7lsraH38uSenCz9DA.gif)

Check out a bigger image here — [https://github.com/puyanwei/Quark-Text-Editor](https://github.com/puyanwei/Quark-Text-Editor)

**MOO-MOOD — **An iPhone App built using Swift, which records your mood and translates it into useful data. Also includes a machine learning messenger to chat to!

![](https://cdn-images-1.medium.com/max/800/0*bnJKrtbQMY1MaKT-.gif)

[https://github.com/jenniferbacon01/moomood](https://github.com/jenniferbacon01/moomood)

**HELLO WORLD** **— **An auto translating messaging tool built in Python. Now a Chinese person can talk to an Argentinian person, both speaking in their own dialects!

![](https://cdn-images-1.medium.com/max/800/0*F9Fwqse_LcNsErtG.png)

[https://github.com/manoadamro/Mapp](https://github.com/manoadamro/Mapp)

**RECURRIO** — A prototype of a product in which items on a tray can automatically tell if they are empty, in order for products to be reordered automatically. Built using an Arduino board with sensors, as well as an iPhone app built in Swift.

[https://github.com/alessiobortone2/Recurrio3](https://github.com/alessiobortone2/Recurrio3) and [https://www.whitesurwhite.com/recurr](https://www.whitesurwhite.com/recurr)

### AFTERMATHS

Well now that its all over what happens now? Jobhunting! On the day of the presentations there were a bunch of companies that came and pitched to us. We chose some, and have been spending some time filling out their applications.

If we are successful, we will be doing tech tests, and interviews. Our time will be spent possibly looking at other job prospects, learning other languages (React seems like its everywhere), or fixing up our old projects/doing new ones.

![](https://cdn-images-1.medium.com/max/800/0*Ih5WIVyiZzPTaJk1.jpg)

The awesome space for graduates to job-hunt or work in

I have two weeks until I go to Hong Kong, Seoul, and Singapore so if I can land a job that would be great! But no doubt about it, I’m hooked to coding and creating new things so I’ll never stop!

Hopefully I’ll keep up the blogging, I’m really glad I’ve gotten back to it, there are some fantastic memories to look back on and reflect.

![The Graduation Pin!](https://cdn-images-1.medium.com/max/800/1*UaXr-Cbj1BtHf7HPX6f3JA.jpeg)
The Graduation Pin!