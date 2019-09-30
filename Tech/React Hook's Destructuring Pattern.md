The other day I was reading up on the legendary React God Dan Ambrov’s great but very un-TLDR [post on useEffect](https://overreacted.io/a-complete-guide-to-useeffect/#dont-lie-to-react-about-dependencies).

![Street art in Shoreditch, London. Sometimes I fake it til I make it, but it can come back and bite me in the](https://cdn-images-1.medium.com/max/800/1*QD_Xet1q1I5FO8C5dBwWPg.jpeg)
Street art in Shoreditch, London. Sometimes I fake it til I make it, but it can come back and bite me in the

The transition to Hooks has been quite a confusing one actually, as most people assumed (including myself) that the changes were just about the syntax. In fact, the changes are more substantial and it involves rethinking ifecycles and how we restructure the components. This \[in progress…\] [post](https://wattenberger.com/blog/react-hooks) shows us the kind of rethinking that are needed…

### A UseEffect Counter Refactor

The post talks about how this is not correct, the count will always be zero.

```
const Counter = () => {  const [count, setCount] = useState(0);  useEffect(() => {    const id = setInterval(() => {      setCount(count + 1);    }, 1000);    return () => clearInterval(id); // Cleanup on 'unmounting'  }, []);  return <h1>{count}</h1>;}
```

However putting a watcher on the count state will allow the effect to update correctly.

```
useEffect(() => {  const id = setInterval(() => {    setCount(count + 1);  }, 1000);  return () => clearInterval(id);}, [count]);
```

This is pretty much going to be the most common way that most of us will conclude with. But Dan Ambrov says that we can level up with another way which would remove the watcher completely!

```
useEffect(() => {    const id = setInterval(() => {      setCount(c => c + 1);    }, 1000);    return () => clearInterval(id);  }, []);
```

Amazing!

However, if your like me and have been too lazy to fully understand React’s hooks array destructuring then your probably asking…

> Where on earth does that “**c**” come from?

### A ‘New’ Trending JS Pattern

Maybe not so new, but new to a lot of us and hooks has popularized it to new levels!

```
const [state, setState] = useState(init);
```

_useState_ is a function that returns an array of functions…

For example we could mock it up like this;

const useState = (initialState) => {  
 return \[state(initialState), setState(initialState)\]  
}

const state = (parameter) => {  
    return \`this is the state function with the parameter - ${parameter}\`  
}

const setState = (parameter) => {  
    return \`this is the setState function with the parameter - ${parameter}\`  
}

Invoking use_State_ would get us;

**useState(99)**  
(2) \["this is the state with the parameter - 99", "this is the setState with the function parameter - 99"\]

**useState(99)\[0\]**  
"this is the state with the parameter - 99"  
**useState(99)\[1\]**

"this is the setState with the parameter - 99"

**useState(99)\[2\]**  
undefined // Element doesn't exist

Destructuring allows us to rename the returned elements as what they are name to represent themselves

**const \[state, setState\] = useState(99)**

// Equivalent to...

**const state = useState(99)\[0\]**  
**const setState = useState(99)\[1\]**

But in this instance we get an error;

_Uncaught SyntaxError: Identifier ‘state’ has already been declared_

This is because we already have used the name _state_ in our function expression inside _useState._

Actually we can use any name we want (that isn’t already used) to represent the first two elements of the returned array from _useState_;

**const \[whatIsTheState, changeUpDatState\] = useState(99)**

**whatIsTheState  
**"this is the state with the param - 99"

**changeUpDatState  
**"this is the setState with the param - 99"

Thanks to Ken C Dodds on his [post](https://kentcdodds.com/blog/react-hooks-array-destructuring-fundamentals) on helping me understand this.

### Rosetta Stone That Counter

Aight, lets go back to that counter;

```
const Counter = () => {  const [count, setCount] = useState(0);
```

```
  useEffect(() => {    const id = setInterval(() => {        setCount(c => c + 1);          }, 1000);      return () => clearInterval(id);    }, []);
```

```
    return <h1>{count}</h1>;}
```

_c_ is the parameter of setCount, which is the initialState of useState, which is 0 for the first time round.

One is added to _c_ and then is returned as the param for setCount, which sets the new count. This happens every second.

This means that useEffect is run once on load, and there is no need to keep calling useEffect on each change, as it is all happening once.

### Custom Hooks Potential

The power of this pattern is that it has ton of potential when you start using custom hooks. Features can be abstracted out of the components and have only the relevant data returned within those arrays to be used.

const \[name, age, error\] = useCustomerDataAPI(key)

Here this made up custom hook can be setup like this. The hook needs an api key as a parameter and then will return 3 functions which returns a name string, a number age and a boolean error.

These three functions are able to be used in our component, most likely using error to check if it is false and then rendering the name and age to the page.

I wont go into details of the custom hook itself, will probably require another post. For now, I’m really enjoying the direction that React is going…

![Also getting bored of all the same unsplash images that everyone is using, might just add in more personal Street Art photos that I take around London!](https://cdn-images-1.medium.com/max/800/1*Ixa4JX92ELxH9K6KZRK5Gw.jpeg)
Also getting bored of all the same unsplash images that everyone is using, might just add in more personal Street Art photos that I take around London!

Til next time folks, happy coding!