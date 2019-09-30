---
title: Hooked on React Hooks — useState
description: >-
  So what’s all the rage with React hooks? I’ve been exploring it for the past
  few months and lets just say I really believe that this is…
date: '2019-05-13T07:29:25.542Z'
categories: []
keywords: []
slug: /@pyan/hooked-on-react-hooks-usestate-53d771214d80
---

![Photo by [Dave Phillips](https://unsplash.com/@teracomp?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)](https://cdn-images-1.medium.com/max/800/0*0G-DQYbrauyBSwGA)
Photo by [Dave Phillips](https://unsplash.com/@teracomp?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

#### Let’s Get Setup!

Setup your project as shown in this [post](https://hackernoon.com/reacting-to-react-js-10ff1d50a36c).

Then lets `npm install --save react@^16.8.0 react-dom@^16.8.0`

If your adding this to an existing codebase its super important to make sure that the `react` and `react-dom` versions are the same. We had some issues where if was throwing an error from the server side not recognising hooks.

#### setState becomes useState

Here we have a component ColourPicker. It toggles between the three colours chosen, with the default on red.

import React, { Component } from 'react';

import './ColourPicker.css';

class ColourPicker extends Component {  
    constructor() {  
        super();  
        this.state = {  
            colour: 'Red',  
        };  
    }  
      
    colourChoice = (colour) => {  
        this.props.handleColour(colour);  
        this.setState({ colour: colour });  
    };  
      
    render() {  
        return (  
            <div className="colour-picker">  
                <p>  
                    Colour:{' '}  
                    <span className="picker-choice">{this.state.colour}</span>  
                </p>  
                <button onClick={() => this.colourChoice('Blue')} />  
                <button onClick={() => this.colourChoice('Cyan')} />  
                <button onClick={() => this.colourChoice('Pink')} />  
            </div>  
        );  
    }  
}  
export default ColourPicker;

When a button is clicked, it triggers the propped function handleColour from the parent component which will do something there. Now lets check out the React hooks refactor;

import React, { useState } from "react";

import "./ColourPicker.css";

const ColourPicker = ({ handleColour }) => {  
    const \[colour, setColour\] = useState("Red");

    const colourChoice = (colour) => {  
        setColour(colour);  
        handleColour(colour);  
    };

    return (  
        <div className="colour-picker">  
            <p>  
                {\`Colour: \`}  
                <span className="picker-choice">{colour}</span>  
            </p>  
            <button onClick={() => colourChoice("Blue")} />  
            <button onClick={() => colourChoice("Cyan")} />  
            <button onClick={() => colourChoice("Pink")} />  
        </div>  
    );  
};

export default ColourPicker;

First thing we should notice is that we import useState at the top. This is how you import each hook that you want to use.

Next you should notice this line;

const \[colour, setColour\] = useState("Red");

This array destructuring is going to be the format we use the old setState with. There are three parameters we want to add in for every state we want to use, the name of the state, the function name of changing the state, and the state’s default value.

const \[stateName, setStateNameNewState\] = useState(defaultValue);

With this in mind, check out the function colourChoice that is called on click;

const colourChoice = (colour) => {  
    setColour(colour);  
    handleColour(colour);  
};

compared to the old

colourChoice = colour => {  
        this.props.handleColour(colour);  
        this.setState({ colour: colour });  
    };

As you can see its much nicer readable syntax.

There is no need to always put in a key: value pair anymore, and notice the lack of `this` and `this.props` keywords! So much better!

#### Stuff I Like

*   **Consistent written components** — If everything is pure functions, having this consistency is great. This will make React easier to learn and understand. There’s nothing worse then when you start out learning trying to get your head around `jsx` syntax, then have it be recommended to write pure functions when you can mixing with the `Class` syntax.
*   **Better syntax** — Even with the simple example above, you can see how much space is saved, without compromising on the readability of the code. Extra destructuring is not needed. With larger apps, having no `this`, `state`, or `props` keywords can mean a lot more lines code saved which in turn can lead to less syntax and scoping mistakes.
*   **Easier to understand, better readability **— This should make code more readable and quicker to understand without all the necessary clutter

#### Cons

*   **Weird / advanced syntax**? — Having this destructured format might be confusing for newer developers. However, React typically has a lot of newer ES6 features which are essential for a smoother experience.
*   **Adds more ways of doing things** — Living in Javascript-land, this is a common thing. But I think it can get out of control, especially for new learners. It is quite common to find old deprecated solutions and then find out later down the line that you have done things incorrectly.

**Useful References**

There are some great docs about React and hooks, check out these awesome references if you wanna read more.

*   The official React docs — [https://reactjs.org/docs/hooks-intro.html](https://reactjs.org/docs/hooks-intro.html)
*   Dan Abrov’s awesome blog — [https://overreacted.io/](https://overreacted.io/)
*   Examples of common components using hooks — [https://usehooks.com/](https://usehooks.com/)
*   Amazing illustration explanation of React (and other code related things) — [https://illustrated.dev/](https://illustrated.dev/)

Next post we’ll check out how hooks deal with lifecycle hooks.