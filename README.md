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


#### 3 Display Output in React with a Component's render Method


#### 4 Set Properties on React Components
### Props
We pass data to components using props. props is how we pass data
around in React.

```javascript

ReactDOM.render(
  <App txt="this is prop" />,
  document.getElementById('root');
)
```

```javascript
class App extends React.Component {
  render() {
    return(
      <div>
    <h1>Hello Emeka </h1>
    <p>Love you </p>
    </div>
    );
  }
}
```
### propTypes

We can define the properties our component is looking for by adding
propTypes

App.propTypes = {
  txt: React.propTypes.string,
  cat: React.propTypes.number.isRequired
}

#### defaultProps

App.defaultProps = {
  txt: "this is default text"
}


#### 5 Manage React Component State with setState