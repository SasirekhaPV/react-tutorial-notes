### A Course Note on React

Course Title: [Start Learning React](https://egghead.io/courses/start-learning-react)

Course Author: [Joe Maddalone](http://joemaddalone.com/#/)

Course Platform: [Egghead](egghead.io)

Course Price: Free

#### 1 Use create-react-app to Setup a Simple React App
To work with React, we can use the `create-react-app` package on `npm`.

Follow the steps below to install the package and  setup a react app.

1. Run `npm i -g create-react-app` to install globally on your machine.
2. Run `create-react-app dir_name` to create app. In my case, directory name is `react-app`
  but you can use whatever name you want.
3. `cd react-app` and run `npm start` to run the app. This should open the browser to `localhost:3000/` where you see the React welcome page.
4. Great! Stop the app for a while and go to step 5.
5. Remove all files in the `src` directory except for the App.js and index.js file.
6. Also edit the `index.html` file in the `public` directory to this content:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>React App</title>
</head>
<body>
  <div id="root"></div>
</body>
</html>
```
7. Finally, remove the `import ./style.css` call from `App.js`

__A little explanation of the `import` s in `App.js` file:__

`import React from 'react'` => This imports React, which is the library that allows us to builds components.

`import ReactDOM from 'react-dom'` => imports ReactDOM, Which is the library that allows us to place the components and work with them in the context of the DOM.

`import App from './App'` => Import the App component which is defined in `App.js`


#### 2 Write a "Hello World" React Component
From the [official React doc](https://reactjs.org/docs/components-and-props.html) :

>Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.   
Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.

##### How to create components
1. Class Components

```javascript
class App extends React.Component {
  render() {
    return <h1 className="hello-world">Hello World </h1>
  }
}
```
**Notes**

- A class component can have a number of attributes or methods. The `render` method must be present
- The `render` method is what, well, renders the component to the DOM.
- The expression inside the `render` method above looks like `htm` but it is actually called `JSX`, syntax extension to JavaScript. In fact, see the [docs](https://reactjs.org/docs/introducing-jsx.html) for more on `JSX`.
- All `JSX` get compiled down to Javascript: `React.createElement()` calls to be specific.


2. Function components

Simplest way to define a component is via Javasccript function. Like below:

```javascript
function App(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
or `ES6 style`:

`const App = () => <h1>Hello World </h1>`

**Notes**

- As shown above, you can pass `props` or not. We discuss `props` below.
- Function components are stateless. We look at state below as well. Sorry for getting ahead of myself.

#### 3 Display Output in React with a Component's render Method

**Notes**
- To return more than one element in a `render` method, you need to wrap it with a parent element. Like this:

```javascript
render() {
  return (
  <div>
    <h1>Hello World </h1>
    <b>Bold</b>
  </div>
  );
}
```

- Also use enclosing parenthesis, to avoid the pitfalls of [automatic semicolon insertion](https://stackoverflow.com/questions/2846283/what-are-the-rules-for-javascripts-automatic-semicolon-insertion-asi)


#### 4 Set Properties on React Components
__Basics of setting properties(props) in React components__

Props is how we pass data
around in React. We pass props to the component like below:

```javascript

ReactDOM.render(
  <App txt="this is prop" />,
  document.getElementById('root');
)
```
- In the example, we pass a prop called `txt` to the `App` component. 
- It looks a lot like html attributes, syntax-wise.
- In the component, we can access the props by interpolating with curly braces like below:

```javascript
class App extends React.Component {
  render() {
    return <h1>{this.props.txt}</h1>
  }
}
```
### propTypes

We can define the properties our component is looking for by adding `propTypes`:

```javascript
App.propTypes = {
  txt: React.propTypes.string,
  cat: React.propTypes.number.isRequired
}
```
- This is an object in which the key is the `prop` and the value is the type of value we want the `prop` to have.
- We can also append  `.isRequired` to a `propType` to show that it is required. Right.

#### defaultProps
We can set default props using, well, `defaultProps`:

```javascript
App.defaultProps = {
  txt: "this is default text"
}
```


#### 5 Manage React Component State with setState