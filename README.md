###Course Note for Start Learning React
A course on egghead.io by Joe Maddalone

###unit 1: Setting up
=========
1. install create-react-app, a tool for quickly scaffolding react app.
  Run `npm i -g create-react-app` to install globally.
2. Create react app. Run `create-react-app folder_name` to create app.
3. Remove all files in the src folder except for the App.js and index.js file.

### Components

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
###propTypes
We can define the properties our component is looking for by adding
propTypes

App.propTypes = {
  txt: React.propTypes.string,
  cat: React.propTypes.number.isRequired
}

####defaultProps

App.defaultProps = {
  txt: "this is default text"
}
