Wassup all, hope everyone is enjoying the new year. 2019 feels like such a crazy number, we are sooo past that Back to the [Future](https://hackernoon.com/tagged/future) 2015 fantasy world!

Gonna do some [react](https://hackernoon.com/tagged/react) snippets since I’m using it the most at work these days. I still do think that Vue is superior, especially for this example.

### Aim

Grab the value of the input box in real time and store it to be potentially used later.

### Setup

If your not sure about the initial setup for react, check out my blog post on using [create-react-app](https://hackernoon.com/reacting-to-react-js-10ff1d50a36c).

I stripped off all the defaults and put this in to check its working. Don’t forget to run `npm start`\` to start your page on localhost/3000. It should pop up automatically.

App.js looks like

import React, { Component } from 'react';  
import './App.css';

class App extends Component {  
 render() {  
  return (  
   <div className="App">  
    <h1 className="element">hello this is the initial setup!</h1>  
   </div>  
  );  
 }  
}

export default App;

I added a lil centering css in App.css

.App {  
 text-align: center;  
 height: 100vh;  
 width: 100vw;  
 display: grid;  
}

.element {  
 display: inline-block;  
 margin: auto;  
}

Should look like this

![](https://cdn-images-1.medium.com/max/800/1*gHw3yD8eBYZg_n3FHy38Gw.png)

With this file structure

![](https://cdn-images-1.medium.com/max/800/1*f5a_NZv0KpKX89Ebz3lRgw.png)

### Make the text box

import React, { Component } from "react";  
import "./App.css";

class App extends Component {  
  render() {  
    return (  
      <div className="App">  
        <div className="element">  
          Tell me your darkest secrets! <input type="text" />  
        </div>  
      </div>  
    );  
  }  
}

export default App;

Should make it look like this

![](https://cdn-images-1.medium.com/max/800/1*sO2XaCmLMWVvmT91vGPHEg.png)

### State Logic

Aight, so now we need to have the value of the text box be stored somewhere. In react’s case we should use `this.state= {value: ''}`\` which uses a key/value pair hash to store our data. We set the value attribute of the text box to refer to that value which is `this.state.value`.

import React, { Component } from "react";  
import "./App.css";

class App extends Component {  
  constructor() {  
    super();  
    this.state = { value: "" };  
  }

render() {  
    return (  
      <div className="App">  
        <div className="element">  
          Tell me your darkest secrets!  
          <input type="text" value={this.state.value} />  
        </div>  
      </div>  
    );  
  }  
}

export default App;

Right now, we can’t actually type anything in there because the value of the text box is set to ‘ ’ in `this.state.value` so we have to add some code to update it to whatever the user types.

We add in a custom function to that runs on every change in the text box to update the value of it. When you update the state in react, we use `this.setState = {key: value}` and rewrite the state hash.

handleTextboxValue = event => {  
    this.setState({ value: event.target.value });  
  };

and in the `input`tag add this attribute

<input  
            type="text"  
            value={this.state.value}  
            onChange={event => this.handleTextboxValue(event)}  
          />

We can actually remove `event`from the attribute as its explicit. The final code should look like this;

import React, { Component } from "react";  
import "./App.css";

class App extends Component {  
  constructor() {  
    super();  
    this.state = { value: "" };  
  }

handleTextboxValue = event => {  
    this.setState({ value: event.target.value });  
  };

render() {  
    return (  
      <div className="App">  
        <div className="element">  
          Tell me your darkest secrets!  
          <input  
            type="text"  
            value={this.state.value}  
            onChange={this.handleTextboxValue}  
          />  
        </div>  
      </div>  
    );  
  }  
}

export default App;

If you install the react app chrome extension, you should be able to see the state updating live.

![Photo by [Ian Parker](https://unsplash.com/@evanescentlight?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral). That feeling you get when something works!](https://cdn-images-1.medium.com/max/1200/1*JyWgDrxjbZi3bOzEuR93JQ.gif)
Photo by [Ian Parker](https://unsplash.com/@evanescentlight?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral). That feeling you get when something works!

![That feeling you get when something works!](https://cdn-images-1.medium.com/max/800/0*plF7SwfOCuEFIPVf)
That feeling you get when something works!

Hopefully this is helpful and clear, I’ll try and make another snippet next week. Have a great week guys!