So for the past few weeks or so, I had been working on a Single Page App (SPA) that I had [previously done](https://thep-log.blogspot.co.uk/2017/09/makers-week-seven-single-page-app.html) during the course. Back then we had a choice which was to do a more open direction version in groups, or work on a more directed path in pairs. I had chose the groups option, so I decided to go back and have a look at what the pairs did.

This project was done in basic Javascript only. This meant that we would only use the the core functions of the language and not have any add ons or libraries to help us. We were limited to using Javascript, HTML, DOM elements, CSS and only Node.JS’s http server to run a local server.

**WHAT IS A SPA?**

A single page app is a webpage application which includes some functionality that works without needing to reload the page. This can be done by modifying the page live according to what is wanted. This means that once the initial page is loaded, all of the functionality should work without needing to have a server respond to requests from the page. Pages like Github or Gmail are SPA’s.

![My app lists out the notes but limits it to 20 characters](https://cdn-images-1.medium.com/max/800/0*uM7ASv0G0R-BhzQj.png)
My app lists out the notes but limits it to 20 characters![Clicking a note will show it in full](https://cdn-images-1.medium.com/max/800/0*WB3as8qMsrCF04Dn.png)
Clicking a note will show it in full

Note that reloading the page manually will reset everything.

**LISTENING OUT**

The DOM contains something called Event Listeners which are used to only run your function when an “event” happens on the page. For the app we had 2 event listeners.

One listener listens for the create button being pressed. When this happens, it will take the text from the text box, and output a list containing the first 20 characters to the page. It adds all this HTML inside the <div id=app> tags.

![](https://cdn-images-1.medium.com/max/800/0*wzqmPvT3Azw5m9S7.png)

The other listener listens for a ‘hashchange’ in the url. When a note is clicked, the link will change the url. When this happens, it will run a function that looks at the number in the url, and output the correct note to the page in full. Again, this edits the <div id=app> tags and adds in the correct HTML.

![](https://cdn-images-1.medium.com/max/800/0*AzbCHELJJOdC3AEZ.png)

**MVC STRUCTURE**

The notes app is encouraged to maintain a MVC structure. This stands for Model, Views, and Controller.

*   **Models** are the logic behind the app.
*   **Views** are the output of the app, what the user sees.
*   The **Controller** is where everything is linked together and implemented.

![Keeping the file structures to MVC](https://cdn-images-1.medium.com/max/800/0*L-PycPr_Xnl0DSv8.png)
Keeping the file structures to MVC

In my app the models would be the list of the notes, and the notes itself. The note inputs would be stored here to be referred to.

The views would be the conversion of the model’s notes into HTML so that it can be output into the page.

The controller would control all of this, and initiate the functions when applicable according to the events it listens to.

This also means that the html page itself can be considered a controller too, as all the files are loaded and initialised within it.

**TESTING**

One of the scariest parts of the project was to build your own testing framework to use to test the SPA. Previously we had been using pre-made ones like RSpec or Jasmine, and never really thought about how they worked.

But once we broke it down, we realised that tests were just comparisons between things, and then outputting true or false.

The result could then be outputted to the console, and then later on I outputted it to the page itself.

I made a homage to a common testing framework used called “Mocha” and called mine “Espresso”

![My own testing framework!](https://cdn-images-1.medium.com/max/800/0*WtiYwt2c0_6702ku.png)
My own testing framework!

**FINAL THOUGHTS…**

My repo is [here](https://github.com/puyanwei/Notes-App-SPA), feel free to have a look. The readme will be more in depth and a bit more advanced technically. Its been really interesting to take this more thorough process with what seemingly seems like a super simple app. I had a lot of [challenges](https://github.com/puyanwei/Notes-App-SPA#challenges) in this project, but found it overwhelmingly useful to my understanding of HTML and Javascript.

![Sometimes a simple question to solve problems can lead to passionate arguments…](https://cdn-images-1.medium.com/max/800/0*xEHlwgfJyvm9MNXu.png)
Sometimes a simple question to solve problems can lead to passionate arguments…

Its super interesting to think about webpages like this, check out this [post](https://medium.com/@NeotericEU/single-page-application-vs-multiple-page-application-2591588efe58) about the pro’s and con’s between SPA’s and multi-page applications. I personally like SPA’s a lot, they load once and then afterwards everything seems instantaneous, creating a free flowing environment to work with.

Well that’s it for now, maybe we can dream of next week having a Singapore post!