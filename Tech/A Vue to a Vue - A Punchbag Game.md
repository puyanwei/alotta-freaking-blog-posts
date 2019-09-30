Y’ello all, hope everyone is good.

This week I’ve been checking out Vue.js and so far I’m loving it! I have done a little bit of React so far, so its not super foreign to me. I’ve been following using this amazing tutorial with the best name ever [Net Ninja](https://www.youtube.com/watch?v=5LYrN_cAJoA&list=PL4cUxeGkcC9gQcYgjhBoeQH7wiAyZNrYa).

Vue.js is a framework for building front end interfaces for the web. It focuses on the view layer only, but is flexible to work with other libraries. It uses a method of rendering data to the DOM (objects on the webpage), which gives it the advantage of being super fast at updating the page.

An example of this would be doing google searches in which it comes up with suggestions before you finish typing. This makes it super reactive, meaning that it runs new searches with each keypress, that is when anything changes on the page.

![](https://cdn-images-1.medium.com/max/800/0*Xjyy4P68PWfn4tzE.gif)

### **Vue the Everyman**

In the industry there are three main front end [Javascript](https://hackernoon.com/tagged/javascript) frameworks. These are Angular, React and Vue. What is interesting is that Angular is developed by Google, React by Facebook, and Vue is not backed by any big tech company.

This means that it lacked the ‘security’ of surviving by having a guarantee that it will be used. This is what makes it more impressive, and because of this, it has to live to a higher standard then its other rivals.

Vue was created by Evan You after working for google using Angular. He has been said to have grabbed the best bits of Angular and React, and combined them into Vue.

Over the past few years Vue has gain traction and big companies are using it more, like Adobe, Alibaba, Expedia, Nintendo and Gitlab to name a few. Developers has rated it highly and it is known for its simplicity (compared to the others), great documentation and welcoming community.

![](https://cdn-images-1.medium.com/max/800/0*HY-KuDt6pSYj5q3b.png)

### **A Minimal Vue.js Setup**

Note that I did follow the tutorial [here](https://www.youtube.com/watch?v=WjfpQlVem-8&index=13&list=PL4cUxeGkcC9gQcYgjhBoeQH7wiAyZNrYa), so its not entirely my work. However I added sounds and the 60’s Batman onomatopoeia (omg thank god for spellcheck) words chosen at random, and some styling as well.

This is what I’ve gotten to so far, this is a super simplistic version because I know there are standardised Vue initialisations which pre generates all your files. Anyways, my thing is all about keeping things simples!

Lets setup! Once we made a project folder and sorted out all ya [github’ins](https://www.youtube.com/watch?v=BCQHnlnPusY&list=PLRqwX-V7Uu6ZF9C0YMKuns9sLDzK6zoiV), we wanna “npm init” press enter a bunch or answer npm’s questions and then “npm install — save http-server”. This downloads the node module for creating a server to run our web app.

![](https://cdn-images-1.medium.com/max/800/0*iyOePL2qYXmKyEza.png)

Go into the package json file and just add this script section to that file. This will make a nice little shortcut for you to only need to type in “npm start” into the terminal to start a server for ya.

Ok so here’s my file structure.

![](https://cdn-images-1.medium.com/max/800/0*JduBqJASnpR3cQ_P.png)

So the two main files we wanna concentrate on are gonna be the Index.html file, which is our front end interface stuff, and app.js which holds some backend logic.

Assets is where I’m keeping my CSS styling of the webpage, and img and sounds folder is some media stuff that I added in later on.

Ok, lets go to the [HTML](https://hackernoon.com/tagged/html) file…

![](https://cdn-images-1.medium.com/max/800/0*mNHzyWJnIuuuxMK6.png)

\*Pro Tip\*(I’m being sarcastic btw coz I’m no pro!), in Atom just write “html” and hit tab, and a basic html structure will be setup for you. This will include the structure above, but without the code inside the head tags, and the body tags.

So inside the head, the “<link rel…” bit is where we’re telling the page to look for the CSS file for the styling. Underneath that in the script tag, that is grabbing the Vue.js file and adding it to our page. This is using CDN which is an online link, but you can download it and refer to your own file like with the CSS.

At the bottom, that script tag is gonna load in our app.js file to the page. More on that later…

So inside the body tag, we’re giving this tag an id “app”. This is where we want Vue.js to render our page. All the elements will go inside this div!

Right, lets go to App.js…

![](https://cdn-images-1.medium.com/max/800/0*oDb12VHizf0Lu11c.png)

So inside this file we wanna put this. Its a new instance of Vue, and it will be structure in a hash table. So remember, when we add lines we need commas, apart from the last line of every hash!

Inside this Vue instance, each hash represents something. The “el” represents the element we are rendering to, in this case that div tag with the id “App”, this is the bridge that links App.js to Index.html.

Data represents variables that we can refer to and/or change, and methods are well, exactly that, functions that “do stuff”

### **Building The Punching Bag**

Ok, gonna zoom ahead and try and challenge myself to explain this!

![](https://cdn-images-1.medium.com/max/800/1*Gk8dZkZ_JLzD7cQmWIKVVQ.gif)

The structure has a title at the top, then some text, followed by a picture, a lifebar, and then our buttons “Punch” and “Restart” at the bottom. Here’s our final App.js;

![](https://cdn-images-1.medium.com/max/800/0*LbYluowDUIONYolQ.png)

Ok, so yeah this looks like a lot of stuff to take in.

The data hash contains some of our variables;

**“health**” — which starts at 100 initially.

**“ended** “ — which is a boolean, ie true or false.

**“batman**” — an array of hilarious words from the 60s batman series I got from this [awesome website](https://www.fastcompany.com/3055253/every-batman-fight-scene-onomatopoeia-in-one-alphabetical-gif) which listed all of them. The list is a loooot longer!

**“chosenWord**” which is blank at first and that’s what the selected word will be.

The methods section which contains our functions;

**“playPunch, playKnockout” **— These dudes load up our sounds files and plays them.

**“punch**”- deducts 10 from our health variable, and checks to see if the health below is one. If it is then it sets ended to true. Then runs the playKnockout function which plays the fainted and knockout sounds.

**“restart**”- this sets the health variable back to 100, and makes the ended variable false again. It then resets the chosenWord variable to being blank.

**“pickWords” **— chooses a random number between 0 and the length of the array, grabs that element word, and then applies it to the chosenWord variable.

Phew! Still with me? Lets continue…

![](https://cdn-images-1.medium.com/max/800/0*K-oinpH-ml1cLba8.png)

Ok, so the html page is sectioned out as mentioned above. There are some really cool Vue variable and event syntax stuff to check out!

*   Variables in our data hashes can be referred to through using { \[variable key pair name\]}. Vue will look through the hashes and find that name.
*   You can output the contents of the variable using {{ \[key pair name\]}}. For example here we can output the health like <p>{{ health }}</p> which would output 100. EZ!
*   “:” is short for “v-bind” which binds that website property to the variable output.
*   DOM Events are shorcutted to @ symbols, so here notice how easy it is to setup the @click event.

**Bag Image** — This line is saying that if ended = true, then add the burst class to this tag.

![](https://cdn-images-1.medium.com/max/800/0*m63gkzwZ8nFwUShf.png)

In our CSS file, we have an attribute where #bag.burst will show a different picture to #bag. So when the ended variable becomes true, the picture changes.

**Bag Health** — Here we use another bit of CSS magic to create a dynamic life bar;

![](https://cdn-images-1.medium.com/max/800/0*NPhsmLbmrH7uoz7W.png)

Here #bag-health is our black border, and #bag-heath div is our red life bar. This life bar is linked with the variable health, and its width attribute changes in relation to how much health it has.

![](https://cdn-images-1.medium.com/max/800/0*ins7aBdOmd8yih_X.png)

**Game Controls** — Here is an example of how easy the event handlers are. @click, which is when the buttons are clicked, runs those functions named in the methods hash.

Button Punch — Runs methods punch, playPunch and pickWords.

Button Restart — Runs method restart.

Interestingly enough, you don’t normally need the () brackets to call the functions as Vue will just look for the names. But one of the struggles I had was to get multiple functions running in one click event, and for that reason I think it might need them there. But I’m not 100% sure.

**Batman Words** — This is where the output of the randomly chosen batman word goes. Notice the syntax of how simple it is; {{ chosenWord }} outputs that variable!

So there you have it, a simple app to start you (or me) out. Its interesting that there is a lot more logic being put on the html page now, it seems that is the direction that technology is moving towards these days…

![You can see how dynamically the code changes elements on the page](https://cdn-images-1.medium.com/max/800/0*0TVIuVThQ4vlyFtK.gif)
You can see how dynamically the code changes elements on the page

My full repo is [here](https://github.com/puyanwei/punchbag-game), have a look and enjoy! I’ll be doing more Vue-y style things this week, looks like a lot of potential! Have a great week peeps!

\*\*Update! I managed to upload it to heroku [here](https://punching-bag.herokuapp.com/).