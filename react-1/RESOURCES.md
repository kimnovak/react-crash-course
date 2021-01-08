# Lesson 1

React is a JavaScript library for building user interfaces.

Official website is: https://reactjs.org/

When you open the official website you will see 3 main characteristics of React:
1. Declarative
2. Component-Based
3. Learn Once, Write Anywhere

## React is Declarative

What is meant by this is that we will only be responsible of saying that we want the DOM to update, but we will not be responsible for HOW that happens. React will handle this for us.  

Without React if we wanted to update data we would do something similar to this   
   
//before    
```<div id="element-to-update">Content</div>```  
   
//on some event   
const element = document.getElementById('#element-to-update');   
element.innerHTML = 'New Content';   

//result
```<div id="element-to-update">New Content</div>```    

With React we would (technically) create a variable and just update the value of that variable. React will handle DOM updates and we will end up with the same result as the one in the example before

```<div>{content}</div>```    

```let content = 'Content';```      

//before    
```<div>Content</div>```     

//on some event  
```content = 'New Content';```   

//result  
```<div>New Content</div>```   

This is how it would really look in React:  
```
class MyComponent extends React.Component {
    state = {
        content: 'Content'
    }

    componentDidMount() {
        this.setState({
            content: 'New Content'
        });
    }

    render() {
        const {content} = state;
        return (
            <div>
                <div>{content}</div>
            </div>
        )
    }
}
```

Initial value of content is 'Content' but as soon as the component mounts it changes to 'New Content'
No DOM manipulation is done by us, we only update data

Data that changes over time is stored inside Component's State
componentDidMount is a lifecycle hook, it gets called on a specific event - the moment that our component is mounted to the DOM
More on both of these topics later

## React is Component-Based

What is meant by this is that the app will be built out of components. We will divide the UI into components. Components can contain other components (child components) and those components can contain child components and so on. Each app has a root component
This means we will have a Components Tree (If you are not familiar with Tree Structure make sure to look it up)

What (from the UI) can be a component? Everything
Should everything be a component? No, you will get a grip of it by time, but for now, everything that seems like a stand-alone logical part should be a component and everything that appears more than once on the screen should be a component

Here's an example

![components](https://github.com/kimnovak/react-crash-course/blob/master/react-1/components.jpg?raw=true)

You can see that side bar item is always built out of 2 elements:  
Icon and  
Label

to render a component in React we would "call" it like this:
```
<SideBarItem />
```
  
We can pass data to the component from its parent  
We call this data ```props```  
More on this later, but for now it looks like this:  

```
<SideBarItem label="Home" icon="home" />
```
The syntax looks like the HTML element and props are sent like HTML element's attributes
  
## Learn Once, Write Anywhere  
With React you can create Client-side Web apps, but that's not all you can do.  
You can also create mobile apps using React Native which is a bit different but it is REACT so the syntax and how it works is the same.  
You can also render React on the server side.  

# Lesson 2
Time to create our first app!

You will need Node and npm for this Download & Install from nodejs.org

In the Directory and CLI of choice run this command:
```npx create-react-app my-first-app```  //Not sure what npx is? Learn about it here: https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b  

To run the project change position to the project's directory:  
```cd my-first-app```
and then run:  
```npm start```  

It should automatically open a browser tab on http://localhost:3000  

Congrats, you just ran your first React app!  

Next step => Learn about JSX: https://reactjs.org/docs/introducing-jsx.html  
Here are some articles by Kristina Grujic that will help you learn it better:  
https://kolosek.com/react-jsx-loops/  
https://kolosek.com/react-jsx-conditions/  

Now that you know how to write JSX you are ready to write your own components!  

Inside of the App you just created, in src directory, create a new directory and name it components  
src  
-> components  

For smaller projects the folder structure you will encounter is this one:

src  
-> components  
-> containers  
-> pages  

Back to our app, inside of components directory, add a new directory named Button (NOTE: uppercase!). Inside the Button folder create a new file and name it index.jsx  
src  
-> components  
  -> Button  
     -> index.jsx

Using .jsx extension we are saying that this file contains JSX. It should provide better error reporting than .js extension.

Couple of notes:  
1. I am following the AirBnB style guide for React and recommend that you do it too: https://github.com/airbnb/javascript/tree/master/react
2. Components should always be named starting with Capital Letter   
bad - button  good - Button  

Okay back to code:  

Inside index.jsx we are going to add code for our Button component  

Before React v17, every component would start with this line:   

```import React from 'react'```  
This enabled us to write JSX inside of our component.  

But since React v17, if we want to use JSX, we don't have to import React, there is babel transformation that will take care of transforming JSX to JS. Note that if we use something else from React we will need to import it  

### Components

There are 2 ways of writing components, writing them as:  
1. Classes  
2. Functions  
  
Nowadays (since React v16.8 and introduction of React Hooks) projects tend to use only components written as functions and those written before the v16.8 use components written as classes  

What happened with v16.8?  
Before only components written as Classes were able to have state.  
These components are called ```stateful```
Components written as functions couldn't have state 
A component that doesn't have state is called ```stateless``` or ```dummy component```

With v16.8 and React hooks, we are able to have state inside components written as functions too!  
Hooks are easy to understand and from my experience harder to missuse  

Okay, back to code  

We will write our Button component as a function  

```
function Button(props) {
    const {label, onClick} = props;
    return (
        <button onClick={onClick}>
            {label}
        </button>
    )
}

export default Button;
```

Inside App.js add the import for Button:
```import Button from 'components/Button';```  

delete function App and replace it with this: 

```function App() {
  return (
    <Button />
  );
}```
  
Congrats! You just created your first Component!  

Our Component Tree looks like this:

        App 
      /
Button 

This was a short intro to get you started  
Next steps are (THIS IS THE CORE OF UNDERSTANDING REACT):  
Learn about Props:  https://reactjs.org/docs/components-and-props.html
Learn about State & Lifecycle: https://reactjs.org/docs/state-and-lifecycle.html
Learn about Virtual DOM & reconciliation :  
https://bitsofco.de/understanding-the-virtual-dom/  
https://medium.com/@gethylgeorge/how-virtual-dom-and-diffing-works-in-react-6fc805f9f84e


After that learn about Event handling and Controlled input fields and you will be ready to do the task #1
