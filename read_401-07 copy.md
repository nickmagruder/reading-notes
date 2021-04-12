# Welcome to Nick's CodeFellows Page
## CodeFellows Reading Notes

Table of Contents
* [Home](https://nickmagruder.github.io/reading-notes/)



# Code 401 Notes

# Reading 31 - Hooks

## Review, Research, and Discussion
1. Why do we not need more .html pages in a multi-page React app?
  - React can respond (using router) to different URL requests in the same way that having seperate HTML pages of the same name would.
2. If we wanted a component to show up on every page, where would we put it and why?
  - Inside the <BrowserRouter />, outside a <Route /> - allows rendering on any page, no matter the route
3. What does props.children contain?
  - Can contain any data, it is a prop specifically passed to all components for rendering content


## Terms
- Composition
  - How all of one's React components are arrenged and connect to create a cohesive whole.
- Children / Child Components
  - Components nested/under a parent component 
- Hash Routing
  - Using the # of a URL to keep the UI synced with the URL
- Link Routing
  - using React <Link> to create "declarative, accessible navagition" around an application [https://reactrouter.com/web/api/Link](https://reactrouter.com/web/api/Link)
    

<br/><br/><br/><br/>






# Reading 32

## Review, Research, and Discussion
1. What does a component’s lifecycle refer to?
  - How components are invoked/mounted/unmounted; their whole cycle of existance
2. Why do you sometimes need to “wrap” functions in useCallback when called from within useEffect
  - Helps stop a function from being created multiple times
3. Why are functional components preferred over class components?
  - Much less complex, easier to write and test
4. What is wrong with the following code?
```javascript
mport React, {useState, useEffect} from 'react';

function MyComponent(props) {
  const [count, setCount] = useState(0);

  function changeCount(e) {
    setCount(e.target.value);
  }

  let renderedItems = []

  for (let i = 0; i < count; i++) {
    useEffect( () => {
      console.log('component mount/update');
    }, [count]);

    renderedItems.push(<div key={i}>Item</div>);
  }

  return (<div>
     <input type='number' value={count} onChange={changeCount}/>
      {renderedItems}
    </div>);
}
```



## Terms
- state hook
  - A hook that functions similarly to setState(), without combining new and old states into one
- effect hook
  - A hook that "accomplishes" functions, like API calls, or DOM rendering
- reducer hook
  - Lets function components access reducer functions within state management

<br/><br/><br/><br/>






# Reading 33

## Review, Research, and Discussion
1. Describe use cases for useMemo() and useReducer()
2. Why do custom hooks need the use prefix?
3. What do custom hooks usually do?
4. Using any list of custom hooks, research and name one that you think will be useful in your applications
5. Describe how a hook that fetches API data might work

## Terms
- Reducer


<br/><br/><br/><br/>






# Reading 34

## Review, Research, and Discussion
1.Why is the Context API useful?
  - It makes it possible to transmit data through components without having to manually pass props.
2. Can a component outside of a provider get its context?
  -If the context is global
3. What are some common use cases for using the Context API?
  - Anytime global sharing is needed
4. Describe “Context Hell”
  - Since Context API doesn't have as much documentation and standardization, Context Providers can make code difficult to read and understand.

## Terms
- global state
  - State that is kept globally-acessible by being placed at the top of an application
- global context
  - Makes it possible to share data from component to coponent without manually passing through props
- provider
  - "Every Context object comes with a Provider React component that allows consuming components to subscribe to context changes.
  - The Provider component accepts a value prop to be passed to consuming components that are descendants of this Provider. One Provider can be connected to many consumers. Providers can be nested to override values deeper within the tree." 
- consume
  - "A React component that subscribes to context changes. Using this component lets you subscribe to a context within a function component. Requires a function as a child."
  [https://reactjs.org/docs/context.html](https://reactjs.org/docs/context.html)


<br/><br/><br/><br/>




# Reading 35

# Graphs
-  Non-linear data structures made up of vertices that are usually connected by lines called "edges."

## Terms

- Vertex -  Data object that can have zero or more adjacent vertices.
- Edge - A connection of two vertices 
- Neighbor - A directly-connected vertex
- Degree - How many edges a vertex has

## Directed vs Undirected
- Undirected
  - No specific direction to the edges (Facebook)
- Directed/Digraph 
  - Edges go in a specific direction and can potentially go both directions (Instagram)

## Complete, Connected, Disconnected
- Complete - every vertex is connected to every other vertex
- Connected - every vertex has at least one edge (no gaps) (Trees are connected graphs)
- Disconected - Where some vertexes don't have an edge, gaps

# Acyclic vs Cyclic
- Acyclic - no cycles/loops
- Cyclic - loops are possible

# Representation
- Adjaceny Matrix - 2d Array, sparse or dense
- Adjacency List - More common, an array or collection that lists all the vertices a vertex is connected to

# Weighted Graphs 
- Edges have values (speed limits on Google maps routes)
- In a matrix, the "weight" is listed as each edge
- In a list, both the connected vertex and the weight of the connection must be added





<br/><br/><br/><br/><br/><br/><br/><br/>


# Lecture Notes

# Monday 3/22
## Lecture Notes
# React - ~10:50
- Yarn VS NPM 11:18
    - "create-tract-app <appname> --use npm" - SEE LECTURE NOTES
- React Demo - 11:20
- "npm install node-sass" for SASS compatibility - 11:22


<br/><br/><br/><br/>





# Tuesday

##  React Project from GitHub - 10:20
- "git remote -v" check if there is a remote repo in the folder
## Props - 10:34
## Tests - 10:47-11:0
## Deployment - 11:56

```
Success! Created resty at /home/iamnotatgregs/codefellows/401/resty/resty
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd resty
  npm start
```


<br/><br/><br/><br/>





# Wednesday 

# Topics for today:
- Component Lifecycle
- View/Layout Logic


- 9:34 - add "aria" roles (classes) to elements in order to run tests on them
- 9:40 - form submission/debugging - done in Jason's form.js
- 10:04 - different React testing query options

- 10:20 - Conditional Rendering - View/Layout Logic
- 10:26 - Toggle Menu
  - Put it within a component
- 10:51 - CSS CALC - ```calc(50% - 200px)```

## Component Lifecycle - 11:10
- What occurs when a component enters the DOM?
  - componentWillMount: setup phase for the component
    - If something must be done before render, do it here
  - componentWillReceiveProps: component received information from its parent
  - render: occurs in "middle" of component's lifecycle
  ### ^ See lecture notes
## Mocking a Server/Testing 11:35
- MSW - Mock Service Worker (npm)
- Gets brought-in to testing suite
- npm install msw
- Mocking server/writing tests - 11:39
  - in demo under: pokemon.test.js

## Lab
- Add support for PUT, POST, and DELETE in your remote calls - mock tests only 
- Local Storage
- Axios (instead of SuperAgent)


<br/><br/><br/><br/>





## Thursday

##

<br/><br/><br/><br/>





# Friday

## 





# Monday

## Bootstrap
- npm install react-boostrap bootstrap


<br/><br/><br/><br/>

# Tuesday

## Hooks (Custom Hooks)
- 

# Friday
# DSA Graphs
- Linked Lists - Trees - Graphs
- Vetices instead of nodes
- Connections stored in "edges"
- Neighbor: a connection to a single other vertex via a single edge
- Degree: number of edges per vertex
- Directed Graph: edges flow one direction (instagram and twitter)

## Cyclic vs Asyclic
- A graph with a cycle
  - Where edges point back to same vertex in a cycle


## Connected vs Disconnected
- A complete graph will have as many edges as vertices
