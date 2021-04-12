# The Modern React Bootcamp (Hooks, Context, NextJS, Router)
# Also, Max's Academind React Course


# Intro
- Components: reusable parts of a front-end app, primary building-block


# Components
- Can only return one element (but that element can have other child elements nested inside)

# Function vs Class
- Both can accept props and render content
- Histortically, function components couldn't use features like State and lifecycle methods
- With Hooks, we can now write full-featured function components


<br/><br/><br/><br/><br/><br/>




# ES6 JavaScript Refresher
## Exports & Imports
- Default Export:
  - export default person
    -import person from './person.js'
    - can import with a different var name than what its called in the default export
  -No Default export?
    - import { constName } from './example.js';

## Classes, Properties & Methods
- Properties are like "variables" atached to classes
- Methods are like functions attached to classes

## Rest Operator
- Can be used to "spread" multiple arguments (if multiple arguments are passed into a function)
```javascript
const filter = (...args) => {
  return args.filter(el => el === 1);
}

console.log(filter(1, 2, 3));
```

## Destructuring
- Extracting array elements or object properties and storing them in variables

###  Array Destructing
```javascript
[a, b] = ['Hello', 'Max']
console.log(a) // Hello
conosle.log(b) // Max
```

also:
```javascript
const numbers = [1, 2, 3];
[num1, , num3] = numbers;
console.log(num1, num3); 
// 1
// 3
```

### Object Destructuring
```javascript
{name} = {name: 'Max', age: 28}
console.log(name) //Max
console.log(age) //undefined
```

## References & Primitive Types
- Don't try to "copy" an object by just referring to it like so:
```javascript
const person = {
  name: 'max'
};

const secondPerson = person;
```

## Instead do it like this:

```javascript
const person = {
  name: 'max'
};

const secondPerson = {
  ...person
};
```
- properties themselves must be copies other wise "secondperson" just "points" at person, and any changes to person will also change on secondPerson


# Base Features and Syntax (Max)

## Build Workflow
- We want to ship code as small and optimized as possible
- Use NextGen JS
- Using NPM for dependencies
- Use a bundler (Webpack)

## Max's Create React App Config
- "create-react-app react-complete-guide --scripts-version 1.1.5 "

## Max's Components & JSX Cheat Sheet
- Components are the core building block of React apps. Actually, React really is just a library for creating components in its core.

- A typical React app therefore could be depicted as a component tree - having one root component ("App") and then an potentially infinite amount of nested child components.

- Each component needs to return/ render some JSX code - it defines which HTML code React should render to the real DOM in the end.

- JSX is NOT HTML but it looks a lot like it. Differences can be seen when looking closely though (for example className in JSX vs class in "normal HTML"). JSX is just syntactic sugar for JavaScript, allowing you to write HTMLish code instead of nested React.createElement(...) calls.

- When creating components, you have the choice between two different ways:

1. Functional components (also referred to as "presentational", "dumb" or "stateless" components - more about this later in the course) => ```const cmp = () => { return <div>some JSX</div> }``` (using ES6 arrow functions as shown here is recommended but optional)
2. class-based components (also referred to as "containers", "smart" or "stateful" components) => ```class Cmp extends Component { render () { return <div>some JSX</div> } }``` 
- We'll of course dive into the difference throughout this course, you can already note that you should use 1) as often as possible though. It's the best-practice.



# JSX
## Basic Rules
- Allows combining UI and Javascript logic into one file
- Work done by Babel to transpile JSX to JS and html
- JSX is more strict than HTML — elements must either:
  - Have an explicit closing tag: ```<b> ... </b>```
  - Be explicitly self-closed: ```<input name="msg" />```
  - SELF CLOSING TAGS MUST have the ``` /> ```
  - Cannot leave off that / or will get syntax error

## Embedding JS
- just {put it inside curly braces}

## Conditionals
- Esteban Herrera article
- https://blog.logrocket.com/conditional-rendering-in-react-c6b0e5af381e/

- The render() method can return either:
  - a single valid DOM object ```return <div>...</div>```
  - an array of DOM objects (but don’t do this yet!)
  - null (undefined is not ok!)

## You can put whatever logic you want in your render() method for this:
```javascript
class Lottery extends React.Component {
  render() {
    if (this.props.winner)
      return <b>You win!</b>;
    else
      return <b>You lose!</b>;
  }
}
```

## Ternary
```javascript
class Lottery extends React.Component {
  render() {
    return (
      <b>You {this.props.winner ? "win" : "lose"}!</b>
    )
  }
```

## Slots Demo
- demo/slots/Machine.js
```javascript
class Machine extends React.Component {
  render() {
    const { s1, s2, s3 } = this.props;
    const winner = (s1 === s2) && (s2 === s3);

    return (
      <div className="Machine">
        <b>{s1}</b> <b>{s2}</b> <b>{s3}</b>
        <p>You {winner ? "win!" : "lose!"}</p>
      </div>
    );
  }
}
```
- demo/slots/index.js
```javascript
ReactDOM.render(
  <Machine s1="🍇" s2="🍇" s3="🍇" />,
  document.getElementById("root")
);
```

## Layout in JSX
- One component per file
- Then create "App" component that renders everything else into the DOM
- Usually App is the only thing rendered in index.js











<br/><br/><br/><br/><br/><br/>












# Props
- Allows components to be more configurable and customizable
- Properties are immutable; you cannot "update" or add to them.

## Other Props Types
- Numbers must be strings or placed within {curlys}, cannot do just num=3
- Booleans also need curlyes: isFunny = {true}
   - Can also just write "isFunny"
- Repeat something by a prop number:

```javascript
let bangs = "!".repeat(this.props.bangs);
```

- Images 
```javascript
<img src={this.props.img}/>
```

## Looping in JSX
- Most common tool is array.map()

- demo/friends/Friend.js
```javascript
class Friend extends React.Component {
  render() {
    const { name, hobbies } = this.props;
    return (
      <div>
        <h1>{name}</h1>
        <ul>
          {hobbies.map(h => <li>{h}</li>)}
        </ul>
      </div>
    );
  }
}
```

- demo/friends/index.js
```javascript
ReactDOM.render(
  <div>
    <Friend name="Jessica" hobbies={["Tea", "Frisbee"]} />
    <Friend name="Jake" hobbies={["Chess", "Cats"]} />
  </div>,
  document.getElementById("root")
);
```

## Default Props
- demo/hello-3/Hello.js
```javascript
class Hello extends React.Component {
  static defaultProps = {
    from: "Joel",
  };

  render() {
    return <p>Hi {this.props.to} from {this.props.from}</p>;
  }
}
```

- demo/hello-3/index.js
```javascript
ReactDOM.render(
  <div>
    <Hello to="Students" from="Elie" />
    <Hello to="World" />
  </div>,
  document.getElementById("root")
);
```

## Styles
- className instead of class
- HTMLfor instead of for (forms)
- style can take object
- camelCase instead of kabob-case for css

```javascript
  render() {
    const colors = {
      color: this.props.favoriteColor,
      backgroundColor: this.props.otherColor,
    };

    return <b style={colors}>{this.props.message}</b>;
  }
}
```

# Max's Props & State
- props  and state  are CORE concepts of React. Actually, only changes in props  and/ or state  trigger React to re-render your components and potentially update the DOM in the browser (a detailed look at how React checks whether to really touch the real DOM is provided in section 6).

## Props

- props  allow you to pass data from a parent (wrapping) component to a child (embedded) component.

Example:

AllPosts Component:
```javascript
const posts = () => {
    return (
        <div>
            <Post title="My first Post" />
        </div>
    );
}
```
Here, title  is the custom property (prop ) set up on the custom Post  component. We basically replicate the default HTML attribute behavior we already know (e.g. ```<input type="text">```  informs the browser about how to handle that input).

Post Component:
```javascript
const post = (props) => {
    return (
        <div>
            <h1>{props.title}</h1>
        </div>
    );
}
```
The Post  component receives the props  argument. You can of course name this argument whatever you want - it's your function definition, React doesn't care! But React will pass one argument to your component function => An object, which contains all properties you set up on <Post ... /> .

{props.title}  then dynamically outputs the title  property of the props  object - which is available since we set the title  property inside AllPosts  component (see above).



State

Whilst props allow you to pass data down the component tree (and hence trigger an UI update), state is used to change the component, well, state from within. Changes to state also trigger an UI update.

Example:

NewPost Component:
```javascript
class NewPost extends Component { // state can only be accessed in class-based components!
    state = {
        counter: 1
    };  
 
    render () { // Needs to be implemented in class-based components! Needs to return some JSX!
        return (
            <div>{this.state.counter}</div>
        );
    }
}
```

Here, the NewPost  component contains state . Only class-based components can define and use state . You can of course pass the state  down to functional components, but these then can't directly edit it.

state  simply is a property of the component class, you have to call it state  though - the name is not optional. You can then access it via this.state  in your class JSX code (which you return in the required render()  method).

Whenever state  changes (taught over the next lectures), the component will re-render and reflect the new state. The difference to props  is, that this happens within one and the same component - you don't receive new data (props ) from outside!





<br/><br/><br/><br/><br/><br/>







# Create React App Conventions
- Seperate each component into a new file
- Match file name to component name
- Make CSS file for each React component
- add ``` className="House"``` onto House div
- 










<br/><br/><br/><br/><br/><br/>











# State

## "When working with setState(), these are the major things you should know:"
[https://css-tricks.com/understanding-react-setstate/](https://css-tricks.com/understanding-react-setstate/)
- "Update to a component state should be done using setState()"
- "You can pass an object or a function to setState()"
- "Pass a function when you can to update state multiple times"
- "Do not depend on this.state immediately after calling setState() and make use of the updater function instead."

### Thinking About State
- In any sufficiently advanced web application, the user interface has to be stateful.
  - logged-in users see a different screen than logged-out users
  - clicking “edit profile” opens up a modal (pop-up) window
  - sections of a website can expand or collapse, for instance clicking “read more”
- The state of the client interface (frontend) is not always directly tied to state on the server.
- Why would the server need to know if a modal is open?

### State Changes
- State is designed to constantly change in response to events.
- A great way to think about state is to think of games, for instance chess. At any point in time, the board is in a complex state.

# What is React State?
- In React, state is an instance attribute on a component.
- It’s always an object (POJO), since you’ll want to keep track of several keys/values.

## Initial State
- SEE HANDOUT

## super() vs super(props)
- why one and not the other?
- super() required to extend a class/component
- constructor always required when we need state
  - props must be passed-in with super(props) in a constructor that needs props for anything
- When in doubt, just use super(props)

# Changing State
- this.setState() is the built-in React method of changing a component’s state.
- Never directly manipulate the state
- Do not call setState in the constructor

## How it works
- Takes an object describing the state changes
- "patches" the state object - keys not specified do not change
- Async
  - Component will eventually change, but not immediately
  - Component re-renders when its state changes.
  - we can pass in an optional callback function to run once state has updated


- demo/click-me/src/Rando.js
```javascript
class Rando extends Component {
  constructor(props) {
    super(props);
    this.state = { num: 0 };
    this.makeTimer();
  }

  makeTimer() {
    setInterval(() => {
      this.setState({
        num: Math.floor(Math.random() * this.props.maxNum)
      });
    }, 1000);
  }

  render() {
    return <button>Rando: {this.state.num}</button>;
  }
} // end
```

# Click Events in React

- Fixed click:
  - demo/click-me/src/FixedClick.js
```javascript
class FixedClick extends Component {
  constructor(props) {
    super(props);
    this.state = { clicked: false };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({ clicked: true });
  }

  render() {
    return (
      <div>
        <h1>The Button is 
          {this.state.clicked ? 'clicked' : 'not clicked'}
        </h1>
        <button onClick={this.handleClick}>Fixed</button>
      </div>
    );
  }
} // end
```

# State vs Props
- State and Props are the most important concepts in React (after knowing what a “component” is).

term	   structure	 mutable	  purpose
state	   POJO {}	   yes	      stores changing component data
props	   POJO {}	   no	        stores component configuration

## State as props
- A common pattern we will see over and over again is a stateful (“smart”) parent component passing down its state values as props to stateless (“dumb”) child components.
- This idea is generalized in React as “downward data flow”. It means that components get simpler as you go down the component hierarchy, and parents tend to be more stateful than their children.

```javascript
class CounterParent extends Component {
  constructor(props) {
    super(props);
    this.state = {count: 5};
  }
  render() {
    // passing down parent state as a prop to the child
    return (
      <div>
        <CounterChild count={this.state.count} />
      </div>
    );
  }
}
```



<br/><br/><br/><br/><br/><br/>




# Max - Working with Lists and Conditionals
- Slice() without arguments simply returns a new array
 - Better way: spread operator ```[...this.state.person]``` instead of ```this.state.person.slice()```
 - Always give a unique key to 


<br/><br/><br/><br/><br/><br/>




# Max - Debugging React Apps
- Errors!

# Max - Http Request & Ajax
## Axios Interceptors - Interesting!
- Video 171
- For logging, altering headers, etc
## Axios Defaults & Instances
- Video 172




<br/><br/><br/><br/><br/><br/>





# Redux (Max)
## The Redux Flow
- Central Store in each Application
- 3rd Party Library - Stores entire application state
- Redux is about having a clear;y defined process of how your state may change 
- Flow
  - Actions - Dispatched from components
  - State changes will be "reduced" to a single, pure function
  - Subscription model is made subscribing to the central store

## Dispatching Actions
- ```store.dispatch({type: 'INC_COUNTER'});```
- ```store.dispatch({type: 'ADD_COUNTER'});```
- Any other properties can be added:
- ```store.dispatch({type: 'INC_COUNTER', payload, value: 10, etc});```

## Subscriptions
- No need to call getState
```javascript
store.subscribe(() => {
  console.log(store.getstate());
})
```
## Connecting React to Redux
- Create/import store in index.js
- import { createStore } from 'redux';
- npm install react-redux
- import { Provider } from 'react-redux';
- import { Connect } from 'react-redux';
  - a function that returns a Higher Order Component

- How we configure the state:
```javascript
const mapStateToProps = state => {
  return {
    ctr: state.counter
  }
}

export default connect(mapStateToProps)(Counter);
```

## Dispatching Actions from Compenent - 260
- Note: if your dispatch action doesn't need a slice of state, just dispatch null (as first arguemtn in export defualt connect)
```javascript
const mapDispatchToProps = dispatch => {
  return {
    onIncrementCounter: () => dispatch({type: 'INCREMENT'})
  };
};

export default connect(mapStateToProps, mapDispatchToProps)(Counter);
```

# Switch instead of If statements in the Reducer - Video 262
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch)


## Updating State Immutably *Review*- 263
- New state must be made as a copied object with all the new/updated properties (and including the old properties)
- Use Object.assign or spread
  - ...state 
- Use .concat()
  - [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)


## Updating Arrays Immutably - 264
- Possible to make a copy of the array
  - But, objects within an array are still "pointing" to their original object locations
- Better approach .filter() for DELETING
  - ```const updatedArray = state.results.filter((result, index => index !== id);```
    - Filtering through the array and only returning the results that don't have the ID we want to delete
### See 265 for Immutable Update Patterns

<br/><br/><br/><br/><br/><br/>


# Max - Adding Redux to Burger
- 


# Max - Router
## Setting Up Router Package
- npm install react-router
- ``` import { BrowserRouter } from 'react-router-dom';```
- Wrap components in 
```javascript
<BrowserRouter>
 <div>Stuff</div> 
 </BrowserRouter>
 ```

## React router vs react-router-dom
-We installed both react-router  and react-router-dom . Technically, only react-router-dom  is required for web development. It wraps react-router  and therefore uses it as a dependency. 

- We don't need to install react-router  on our own for it to work. You can omit this installation step, I left it in there for historic reasons and because I like to emphasize that the main package is named react-router. If you ever search for assistance, you probably want to search for "react router" - that's the name of the package.

## Setting Up Routes
- App component is wrapped in browser router in app.js
- ``` import { Route } from 'react-router-dom'```
- To create an "Exact" path:

- ```<Route path="/" exact component={Posts} />```

## Links
- Don't use anchor tags
- Use ```<Link>``` component
- ```<li><Link to="/route">-Route</Link></li>```

## Router Props
- ```import { withRouter } from 'react-router-dom';```
- HOC: wrap the export component in "withROuter()" :
- ``` export default withRouter(component);```
- Doing this passes router/history props which can be used later

## Absolute vs Relative Paths
You learned about <Link> , you learned about the to  property it uses.

The path you can use in to can be either absolute or relative. 

### Absolute Paths
By default, if you just enter to="/some-path"  or to="some-path" , that's an absolute path. 

Absolute path means that it's always appended right after your domain. Therefore, both syntaxes (with and without leading slash) lead to example.com/some-path .

### Relative Paths
Sometimes, you might want to create a relative path instead. This is especially useful, if your component is already loaded given a specific path (e.g. posts ) and you then want to append something to that existing path (so that you, for example, get /posts/new ).

If you're on a component loaded via /posts , to="new"  would lead to example.com/new , NOT example.com/posts/new . 

To change this behavior, you have to find out which path you're on and add the new fragment to that existing path. You can do that with the url  property of props.match :

<Link to={props.match.url + '/new'}>  will lead to example.com/posts/new  when placing this link in a component loaded on /posts . If you'd use the same <Link>  in a component loaded via /all-posts , the link would point to /all-posts/new .

### There's no better or worse way of creating Link paths -
choose the one you need. Sometimes, you want to ensure that you always load the same path, no matter on which path you already are => Use absolute paths in this scenario.

Use relative paths if you want to navigate relative to your existing path.

## Styling an Active Route
- Change ```<Link>``` to ```<NavLink>```
- Possible to style "active"
- exact usually needed 
- ```activeCLassName="my-active"``` can be added to props for futher customization

## Switch
- Wrap Routes in ```<Switch></Switch>``` in order to only load the first route that matches

## Router Cont'd ..........




<br/><br/><br/><br/><br/><br/>




# MISC: Convert string to number
- The unary + operator converts its operand to Number type.
 - ```var positiveOne = +1```



<br/><br/><br/><br/><br/><br/>




 # Max's Hooks
 - Hooks must only be used inside functional components, or inside custom hooks
 - Hooks must always be used at the root level
 - Cannot use hook within an if statement or for loop

 #  Hooks Continued
 - ~90 Minutes left @ Deleting ingredients
 







 - 2.8 in 15min
 - 12.5 in 53min