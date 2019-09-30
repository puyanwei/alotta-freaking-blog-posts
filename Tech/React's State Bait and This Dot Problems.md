One of the things that make [React](https://hackernoon.com/tagged/react) quite intimidating for new users is that there are some concepts that need to be grasped before jumping in.

Its important to learn ES6 anyways, but for the patterns and structures used its especially useful for our favourite componentized frameworks. That being said, you can still use ES5 to get it to work, but for the sake of consistency ES6 is the way to go!

![Create websites with React.js!](https://cdn-images-1.medium.com/max/800/0*k8RvKPa9iqlaXM7Y)
Create websites with React.js!

Stop living in the past and move with the times, bruh!! :P

### Don’t Mutate the State, Mate!

Most of the time this isn’t a good idea anyways, but its especially true for building front end projects. Changing the original initiated state can cause a lot of problems when things go wrong, it can make it hard to keep track of where bugs are coming from.

Here we got a shop, lets add an item…

class App extends Component {   
    constructor(props) {    
        super(props);    
            this.state = { shop:\[\] };   
    }

...//

onAdd = (item) => {    
    this.state.shop.push(item);  
};

To the untrained eye this is how you might think to do it. But this is a classic common situation in which we’re changing the original state which is a huge no-no in functional programming.

onAdd = (item) => {   
    let newList = this.state.shop;  
    newList = newList.concat(item);  
    this.setState({ shop: newList })

};

Concat is a method which combines two arrays into a new one. Here we grab the shop array (empty for now) and combine it with the item into a new array. Then we use React’s setState to modify the current state, instead of directly doing it ourselves.

onAdd = (item) => {  
    let newList = this.state.shop;  
    newList = \[...newList, item\];  
    this.setState({ shop: newList })

Most of the time we use the ES6 ‘version’ of combining the arrays with the spread operator. The ‘…’ allows an existing array to be referenced but not modified, meaning we don’t mutate the original array.

Making sure that we never directly mutate the state is great practice, and we want to get in the mindset of doing that all the time.

### Bind Off Your ‘This’ Problems with Arrow Functions

As you may or may not have noticed, the functions written above seem to be in a strange format. Notice there is no function keywords and for more advanced coders therefore no bind methods either.

As we pass data around in our components, we are use the `this.[function]` to refer to functions elsewhere, but because of the lexical scope the `this` isn’t referring to where we want it to.

Arrow functions are a different way of writing functions but with the main advantage of the fact that it stops the `this` keyword from being limited to within that function.

class ParentComponent extends Component {  
    render() {  
        return (  
            <div>  
                <ChildComponent   
                parentFunction="this.parentFunction"   
                />  
            </div>  
        )  
    };

function parentFunction() {  
        console.log("Button is clicked!")  
    }  
}

class ChildComponent extends Component {  
    render() {  
        return (  
            <div>  
                <button onClick={this.handleClick}>  
                    Click Me!  
                </button>  
            </div>  
        )  
    };

    handleClick = () => {  
        this.props.parentFunction();  
    }  
}

Here in this child component we have a button that when clicked, uses the parentFunction props that has been passed down from the parent component.

The fact that parentFunction has been passed down using the `function` keyword will make the `this` keyword not refer to what we want if it has been written without arrow functions.

The ES5 way of solving this problem is to use the `bind` method but this meant every function passed down would have to be bound, and with a lot of function it would not be scaleable.

So just use `[name] = () => {}` to save yourself `this` scoping problems!

Another common scenario is when your DOM events need a parameter.

**Using ES6 Arrow Functions**

```
<button onClick={(event) => this.deleteRow(id, event)}>Delete Row</button>
```

_// Events as parameters are explicit so can be even shorter!_

```
<button onClick={() => this.deleteRow(id)}>Delete Row</button>
```

**Using ES5 Bind**

```
<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
```

Definitely looks cleaner and needs less maintenance. We don’t have to keep track of all our binds, and therefore less prone to mistakes. Its also more readable and looks cleaner overall!

### Get 2 Grips w/ES6!

If you didn’t know these concepts and jumped right in, it definitely can be quite a challenge to understand. Learning the ES6 updates are pretty essential to learning React, which can be quite beginner unfriendly.

Either way, as [Javascript](https://hackernoon.com/tagged/javascript) evolves and defies all the odds and keeps surviving onwards its becoming more apparent that it is important to keep up to date with all the new features added.

These days I try to keep things consistent by using as much ES6 syntax as possible, and Air Bnb linting. The fact that you can do so many things in different ways can be quite daunting for an aspiring newbie.

Anyways, hope that is helpful, have a great week!