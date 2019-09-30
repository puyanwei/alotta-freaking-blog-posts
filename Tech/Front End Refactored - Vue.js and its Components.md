The more I learn about coding, the more inspired I get about how creative and revolutionary some of these ideas are. From the readability of Ruby, to a world of hashes in [Javascript](https://hackernoon.com/tagged/javascript), these ideas keep renewing the way we think and evolve the tech world all the time.

### “No Logic/Coding in Front End”

This was a common stereotype that I noticed was common among up and coming developers at Makers Academy, when consulting them over their job prospects and interests.

![Front End gets a bad reputation for being ‘uninteresting’ because of how people think there is very little coding](https://cdn-images-1.medium.com/max/800/1*-dbbyQwUJz60Znr9SOepQw.jpeg)
Front End gets a bad reputation for being ‘uninteresting’ because of how people think there is very little coding

In our company we have found it very difficult to find a mid and senior level front end developer to join our team. It does make me think about whether this attitude is something that contributes towards developers not wanting commit to the front end.

But recently the front end has been revolutionised with multiple ideas such as CSS grids, the standardisation from Bootstrap and the use of [components](https://hackernoon.com/tagged/components)…

### The Before

Here we show how pages are made up typically.

![Using the dev tools mode in Chrome (Apple + Alt + I and then going to the Elements Tab) shows the HTML code of the page](https://cdn-images-1.medium.com/max/1200/1*KgnAK9J1UPD7bthov4C_-w.png)
Using the dev tools mode in Chrome (Apple + Alt + I and then going to the Elements Tab) shows the HTML code of the page

We put all the elements of the page in between the body tags of the HTML code which outputs to the page.

This seems like a totally fine way of doing thing but the question is, what if had lots of pages and we wanted the header and footer to be on all of them?

We would be copying and pasting that code a lot on each of our pages which would be quite an inefficient way of doing things.

### The Refactor Mindset (In Vue.js)

Whenever DRY (Do Not Repeat Yourself) appears in code, it means one thing… we can refactor it into something reusable, that is referred to!

There are a few suggestions for this such as using partials, but the most popular one over the last few years has been to use Components, as popularised by the Facebook developers using React.js.

Lets look at an example using Vue.js, which is similar to React.js. I like Vue.js because it is more readable and clearer then React imo.

Our components are stored in vue files, and its parent vue file refers to it, usually called App.vue. Each vue file always has the same structure where it is divided into three parts;

<template>  
// HTML of the component goes here  
</template>

<script>  
// Code goes here  
</script>

<style>  
// CSS Styling goes here  
</style>

So lets split up our code and put them into a separate vue file in a folder called components. We’ll take out the footer code and put that into Header.vue. The HTML goes inside the template tags, and we create a variable in the data hash that contains the text.

// Header.vue

<template>  
    <header>  
        <p>{{ headerText }}</p>  
    </header>  
</template>

<script>  
export default {  
    data: {  
        headerText: "This is the header",  
    }  
}

</script>

<style >  
</style>

In our original App.vue file, we refer to that newly created header component we just created.

// App.vue

<template>  
    <div class="container">  
        <br>  
        <app-header></app-header>  
        <hr>  
        <h1>The Article</h1>  
        <article class="article">  
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.  
        </article>  
        <hr>  
        <footer>  
            <p>This is the footer</p>  
        </footer>  
    </div>  
</template>

<script>  
import appHeader from './components/Header.vue'

export default {  
  components: {  
    'app-header': appHeader,  
  },  
};

</script>

<style>  
</style>

In the script, we import that component using the component hash, then we use that name into its own customly named html tag, in this case we called it <app-header>. We can use the name ‘header’ but because that is aleady a tag name that exists we want to avoid these names as to avoid any conflicting code. This is how Vue refers to its components, which is different to React.js.

So lets do the same thing with the Article and Footer section.

// Article.vue

<template>  
    <div>  
        <h1>The Article</h1>  
        <article>{{ articleText }}</article>  
    </div>  
</template>

<script>  
export default {  
    data() {  
        return {  
            articleText: "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."  
        }  
    }  
}  
</script>

<style >  
</style>

Now the footer…

<template>  
    <footer>{{ footerText }}</footer>  
</template>

<script>  
export default {  
    data() {  
        return {  
            footerText: "This is the footer",  
        }  
    }  
}  
</script>

<style lang="css">  
</style>

The final App.vue;

<template>  
    <div class="container">  
        <br>  
        <app-header></app-header>  
        <hr>  
        <app-article></app-article>  
        <hr>  
        <app-footer></app-footer>  
    </div>  
</template>

<script>  
import appHeader from './components/Header.vue'  
import appArticle from './components/Article.vue'  
import appFooter from './components/Footer.vue'

export default {  
  components: {  
    'app-header': appHeader,  
    'app-article': appArticle,  
    'app-footer': appFooter,  
  },  
};

</script>

<style>  
</style>

After all this work, its the same look exactly. But now we have reusable components! This means that any other page we want to create, we can import in those components and use it.

And what is great is that its very easy to tell which component has been imported in, and where in the page it is in by just looking at the template section.

### Front End Revolutionised

Components are super flexible and reusable which are great for huge websites. Even elements such as buttons and forms can be components and therefore reusable throughout.

The styling of each component can also be included within it, which is great for consistency of the branding of the website.

Another reason why components are great is that logic from functions can also be added to each component. This really changed the way websites were created as the logic was typically put in a completely separate place to the HTML. Now, it is added into the component which means that the logic is linked to it right there and can be easier to find.

This means that a lot of the logic is now mixed in with the front end, allowing for a more full stack experience for front end devs and at the same time putting less stress on the the backend which only contains the code that is relevant to what it is trying to do.

![It seems like this will be the battle of the component based Javascript framework! Who will win?](https://cdn-images-1.medium.com/max/800/1*wRC3PA4tW_IJcbFnz5zUug.png)
It seems like this will be the battle of the component based Javascript framework! Who will win?

I hope everyone will have a great May day bank holiday weekend, cya next time!