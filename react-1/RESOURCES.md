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