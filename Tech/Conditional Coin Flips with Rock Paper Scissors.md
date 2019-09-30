In the recent sweltering world heat wave, I was set a tech test the other day. In it I needed to write a function that would output zero to five depending on its 6 combinations. For this example I’ll say we wanna get the outcome of flipping a coin **and** playing rock, paper, [scissors](https://hackernoon.com/tagged/scissors) translated into a number ranging from 0 to 5.

![In Perth I remember seeing a Heads or Tails game in their casino!](https://cdn-images-1.medium.com/max/800/0*1TkMfBBqerG3sbl4)
In Perth I remember seeing a Heads or Tails game in their casino!

Seem simple? Maybe for some, and not so much for others. I try and refrain from calling things ‘easy’ or ‘simple’ because its just all a bit arbitrary. Things are simple for some and not so much for others. All that really does is discourage those who find it hard, and give a little ego boost to those who don’t. This is not helpful in trying to create a non-intimidating, no-questions-are-stupid culture, which will help get more people into [coding](https://hackernoon.com/tagged/coding). #GrindsMyGears.

### Write a Failing Test

Let start by writing a test for it first. This is universally agreed upon of good practice to write tests first before writing code (aka TDD, Test Driven Development). It may seem strange, but this allows a developer to have a good process of thinking how they will write the code out before doing it.

A well tested program will also give the code an assurance of quality and reliability, for when things are added or changed, the tests will give out visibility on where the problems are.

Lets setup [Jasmine](https://jasmine.github.io/). For some strange reason their docs miss out the easiest version of their installation, which is to download a [zipped setup](https://github.com/jasmine/jasmine/releases) and add it to your folder. Once this is done, open it up in your favourite text editor.

![Folder structure of Jasmine standalone. By default there are example files there.](https://cdn-images-1.medium.com/max/800/1*j8n8OWpFaxdwQaxSakMV1g.png)
Folder structure of Jasmine standalone. By default there are example files there.

The `lib` folder is where Jasmine is stored, so don’t worry about that. What we care about is the `spec` and `src` folder. The `spec` folder is where will will write our test, and the `src` folder is where our code will be. Then we will put both files in `SpecRunner.html` so that it will run the tests on your code in the browser by loading that up.

![Opening up SpecRunner shows their default tests](https://cdn-images-1.medium.com/max/800/1*GLVTpesC7UsLGgqUQ9mB3g.png)
Opening up SpecRunner shows their default tests

Aight, lets create our own blank files for the test and the code and put them into the `SpecRunner.html`

![Follow the comments in the SpecRunner.html on where to put your files](https://cdn-images-1.medium.com/max/800/1*sIqmJWDcrlq6gNbvjCZ_ig.png)
Follow the comments in the SpecRunner.html on where to put your files

Lets write our test!

describe('#coinRPS', () => {  
    it('Returns 0 if the coin input is "Heads" and RPS is "Rock"',    () => {  
        let result = coinRPS('Heads', 'Rock');  
        expect(result).toEqual(0);  
    });  
});

Tests are written like this. The `describe` block is a function with the first parameter being a string describing the test. I typically just write #\[function\] to show which function it is talking about. The second parameter is another function `it` which does the same thing as the describe, but this time we write a description in more detail.

The second parameter of the `it` function is another function which will contain our code and the steps to create the outcome we want.

So for our function `coinRPS` we know that we wanna take in two parameters, one for the coin and one for the RPS which will be strings. We also know we want the outcome to return a number from 0 to 5.

Our function `coinRPS` gets called and assigned to `result`. Then we compare `result`’s value and see if that is zero.

It definitely is a super confusing structure with functions inside functions, but if you stick with it you’ll get used to it and hopefully it will be helpful!

Lets check out our test in the browser. Go to SpecRunner and hit refresh.

![Test fails because coinRPS function doesn’t exist yet!](https://cdn-images-1.medium.com/max/800/1*Hm3Wh-bVFzZiS6CMYKU8EQ.png)
Test fails because coinRPS function doesn’t exist yet!

Ok cool. Let write some code in.

function coinRPS(coin, RPS) {  
    return 0;  
}

This will pass.

![First passing test!](https://cdn-images-1.medium.com/max/800/1*YYGFjaiMeUXNkzeAuvWTbA.png)
First passing test!

This process of writing a failing test, then making it pass is what is done for TDD. The next step would be to write one for returning 1. Each small step you take towards your final goal. But for the sake of time, I’ll write a test for all the outcomes.

describe('#coinRPS', () => {  
    it('Returns 0 if the coin input is "Heads" and RPS is "Rock"', () => {  
        let result = coinRPS('Heads', 'Rock');  
        expect(result).toEqual(0);  
    });  
    it('Returns 1 if the coin input is "Heads" and RPS is "Paper"', () => {  
        let result = coinRPS('Heads', 'Paper');  
        expect(result).toEqual(1);  
    });  
    it('Returns 2 if the coin input is "Heads" and RPS is "Scissors"', () => {  
        let result = coinRPS('Heads', 'Scissors');  
        expect(result).toEqual(2);  
    });  
    it('Returns 3 if the coin input is "Tails" and RPS is "Rock"', () => {  
        let result = coinRPS('Tails', 'Rock');  
        expect(result).toEqual(3);  
    });  
    it('Returns 4 if the coin input is "Tails" and RPS is "Paper"', () => {  
        let result = coinRPS('Tails', 'Paper');  
        expect(result).toEqual(4);  
    });  
    it('Returns 5 if the coin input is "Tails" and RPS is "Scissors"', () => {  
        let result = coinRPS('Tails', 'Scissors');  
        expect(result).toEqual(5);  
    });  
});

As you can see there’s quite a bit of repetition here. In programming its good practice to keep code ‘DRY’ (Do not repeat). But for testing its ok, as the aim is to write quality tests first and foremost.

Lets check out some different ways of doing this;

### Six Solutions, The Good, The Bad and The Fugly!

Probably the most common way of doing this is just going for 6 `if statements` straight up;

function coinRPS(coin, RPS) {  
    if (coin === 'Heads' && RPS === 'Rock') {  
        return 0;  
    }  
    if (coin === 'Heads' && RPS === 'Paper') {  
        return 1;  
    }  
    if (coin === 'Heads' && RPS === 'Scissors') {  
        return 2;  
    }  
    if (coin === 'Tails' && RPS === 'Rock') {  
        return 3;  
    }  
    if (coin === 'Tails' && RPS === 'Paper') {  
        return 4;  
    }  
    if (coin === 'Tails' && RPS === 'Scissors') {  
        return 5;  
    }  
}

It passes, enjoy that dopamine hit by seeing this screen on your `SpecRunner`!

![](https://cdn-images-1.medium.com/max/800/1*DBbd8ajrkYVkBbBuom-v8g.png)

It kinda looks similar to a switch statement, lets try that.

function coinRPS(coin, RPS) {  
    switch (true) {  
        case coin === 'Heads' && RPS === 'Rock':  
            return 0;  
        case coin === 'Heads' && RPS === 'Paper':  
            return 1;  
        case coin === 'Heads' && RPS === 'Scissors':  
            return 2;  
        case coin === 'Tails' && RPS === 'Rock':  
            return 3;  
        case coin === 'Tails' && RPS === 'Paper':  
            return 4;  
        case coin === 'Tails' && RPS === 'Scissors':  
            return 5;  
        default:  
    }  
}

Well, that doesn’t actually look like its saved any space at all. In fact it might need a `break` after each return, which seems like a lot more code.

Hmmm that’s a lot of of repetition tho, how about using a kinda tree format?

function coinRPS(coin, RPS) {  
    if (coin === 'Heads') {  
        if (RPS === 'Rock') {  
            return 0;  
        }  
        if (RPS === 'Paper') {  
            return 1;  
        }  
        if (RPS === 'Scissors') {  
            return 2;  
        }  
    }  
    if (coin === 'Tails') {  
        if (RPS === 'Rock') {  
            return 3;  
        }  
        if (RPS === 'Paper') {  
            return 4;  
        }  
        if (RPS === 'Scissors') {  
            return 5;  
        }  
    }  
}

This kinda loses \***some**\* repetition? But what we’ve lost in repetition we seemed to have increased in curly brackets :/

Ok, I’ve heard ternary operators are good at losing brackets, lets try that? Ternaries have the format

`[conditional statement] ? [result if true] : [result if false]`

and I suspect that this will have to use nested ternaries which can be like

`[conditional statement] ? [result if true] : [another conditional statement if false] ? [result if false then true] : [result if false then false]`

Head hurting? Doesn’t look any less confusing…

function coinRPS(coin, RPS) {  
    return coin === 'Heads'  
        ? RPS === 'Rock'  
            ? 0  
            : RPS === 'Paper'  
                ? 1  
                : 2  
        : RPS === 'Rock'  
            ? 3  
            : RPS === 'Paper'  
                ? 4  
                : 5;  
}

But on the bright side there definitely is less brackets, so plenty of points for that! However, for readability I’d say its pretty low down the scale, and thank God I wrote that test to help me out!

Ok, maybe a different approach. Why not write out the outcomes and then match that? #ThinkingOutsideTheBox

function coinRPS(coin, RPS) {  
    let outcomes = {  
        0: 'Heads Rock',  
        1: 'Heads Paper',  
        2: 'Heads Scissors',  
        3: 'Tails Rock',  
        4: 'Tails Paper',  
        5: 'Tails Scissors',  
    };  
      
    let input = coin + ' ' + RPS;  
    let result;  
      
    Object.values(outcomes).forEach((value, index) => {  
        if (value === input) {  
            result = index;  
        }  
    });  
    return result;  
}

Ok so here we got a hash table of `outcomes`. The `input` grabs the string from coin and the string from RPS, and adds a space in between them, just like the strings in the hash values.

`Object.values(outcomes)` loops through the values of our hash table `outcomes`, and if it matches with `input` it will assigns the index number to result, which is our number!

We can do a bit of refactoring with some ES6 template strings, and ternary’ing it up!

function coinRPS(coin, RPS) {  
    let outcomes = {  
        0: 'Heads Rock',  
        1: 'Heads Paper',  
        2: 'Heads Scissors',  
        3: 'Tails Rock',  
        4: 'Tails Paper',  
        5: 'Tails Scissors',  
    };  
    let result;

    Object.values(outcomes).forEach((value, index) => {  
        value === \`${coin} ${RPS}\` ? (result = index) : null;  
    });  
    return result;  
}

Template strings uses backticks \` \` and inside them you use ${} for variables, in this case we can use the parameters coin and RPS passed in.

But wait! You know what? Why not save more precious screen space by using an array instead!

function coinRPS(coin, RPS) {  
    const outcomes = \[  
        'Heads Rock',  
        'Heads Paper',  
        'Heads Scissors',  
        'Tails Rock',  
        'Tails Paper',  
        'Tails Scissors',  
    \];

    return outcomes.indexOf(\`${coin} ${RPS}\`);  
}

`indexOf` is a method which loops through an array and if it finds a match returns the index position of it. Perfect for what we want to do here!

I think one of the toughest things in writing code is to work out the best balance between readability and cleverness. You want it to be code which is able to be understood by the majority of developers, because nearly all coders are working in a team.

People come and go, or maybe you might be returning to some of your own code that you wrote a year ago. I think the nested ternary solution is a good example as a clever solution, but really lacks in readability unless you work ternaries a lot, which probably isn’t the case with most developers.

However its so hard to get this balance right, and different people have different opinions on where they believe this line should be.

Anyways, I’m off to spend hours of fun flipping coins and playing Rock, Paper, Scissors (aka [Hearthstone](https://playhearthstone.com/en-us/)), until next time happy coding peeps!