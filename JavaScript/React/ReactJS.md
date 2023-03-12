

[CodeSandbox](https://codesandbox.io) - handy tool for online dev
[Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react) - Gold standard for code style

A react application is made up of elements that contain other elements. For example:
- Application
	- Header
	- Nav bar
	- Body Container
		- Left menu
		- Content Area
		- Preview Pane
			- Controls
			- Preview content
	- Footer

The HTML page is usually very simple, often only incorporating a single `div` with an ID of `root`. The components are then specified in separate files and rendered nested within the root container or its children.

## Create React App
`npx create-react-app my-app`
`cd my-app`
`npm start`



Import the javascript file with:
```html
<script src="index.js" type="text/JSX"></script>
```

## Importing React
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render( htmlcode, element );
```


## JSX Templates
HTML can be placed directly inside JavaScript code using JSX which is part of React:
```javascript
const rootElement = document.getElementById('root');

ReactDOM.render(
	<div>
		<h1>List of things</h1>
		<ul>
			<li>One</li>
			<li>Two</li>
		</ul>
	</div>,
	rootElement
);
```
*NB: Only ONE element is rendered in the function call. Multiple elements can be incorporated by placing them all in an enclosing container such as the `div` encloses both the `h1` and `ul` above.*

Javascript expressions can be interpolated into the results.
```javascript
var name = "Tony"

ReactDOM.render(
	<div>
		<h1>Hello, {name}</h1>
		<p>Your lucky number is {Math.floor(Math.random() * 100)}.</p>
	</div>,
	rootElement
);
```

### HTML attribute differences
In embedded HTML, use `className` instead of just `class` as an attribute where needed. `class` is a reserved word in JS.

JSX should use HTML attributes in camelCase instead of lowercase (e.g. `contentEditable` vs. `contenteditable` in vanilla HTML)

Empty tags should be either self-closing, e.g. `<br />`

Inline style tags expect a JS object instead of a string
Instead of:
```html
<h1 style="color: red">   <!-- Does not work -->
```
Use:
```javascript
const red = { 
	// NB: camelCase, quoted, commas not semicolons
	color:    "red",
	fontSize: "20px",
	border:   "1px solid black"
}

<h1 style={red}>

// OR

<h1 style={{color: "red"}}>
// one set of curly braces for interpolation,
// one for an object literal.
```

## React Components
Create a function with a name in PascalCase. 
Use that function name as you would an HTML tag.
The initial capital letter marks this as a component.

Before...
```HTML
<div>
	<h1>A List</h1>
	<ul>
		<li>One</li>
		<li>Two</li>
	</ul>
</div>
```

After...
```javascript
function Heading() {
	return <h1>A List</h1>;
}
```
```HTML
<div>
	<Heading />
	<ul>
		<li>One</li>
		<li>Two</li>
	</ul>
</div>
```

Components can be separated into separate files:

`Heading.jsx`
```javascript
import React from "react";

function Heading() {
	return <h1>A List</h1>;
}

export default Heading;
```

`index.js`
```javascript
// ...
import Heading from "./Heading.jsx";  // ext optional in ES6
// ...
```


## Props
```html
<Card
	  name="John Smith"
	  tel="212-555-1212"
/>
```
```javascript
function Card(props) {
	return <div>
		<h2>{props.name}</h2>
		<p>tel: {props.tel}</p>
	</div>;
}
```

## Hooks
Components should render differently depending upon state, but they don't re-render automatically. We use Hooks to tie into the state and force re-rendering of components when the state changes.

### useState

useState returns a 2-element array: one is the value being tracked, and the other is the function that should be called to change this value.

`App.jsx`
```javascript
import React from "react";
import ReactDOM from "react-dom";

function App() {
  // React.useState(init) Returns a 2-element array.
  //   1st element refers to the current value (init)
  //   2nd element is a function to reset the value
  // Assignment syntax creates names from array elements.
  const [count, setCount] = React.useState(0);

  // We use these functions to both read and write count
  function increase() { setCount(count + 1); }
  function decrease() { setCount(count - 1); }

  // count will be re-rendered when it changes.
  return (
    <div className="container">
      <h1>{count}</h1>
      <button onClick={increase}>+</button>
      <button onClick={decrease}>-</button>
    </div>
  );
}

export default App;

```

## Class Components
Older way of doing things. Replaced by Hooks and Functional components.

```javascript
class App extends React.Component {
	render(...)  // instead of return
}
```
Within classes state uses binding and one common `setState` function to manipulate object keys instead of "whole" variables.


## Event Handlers
```javascript
function handleChange(event) {
	// event.target: Object on which the event happened
}
```

## Forms
Do not enclose in form tags or you'll have to use `event.preventDefault()` to prevent a page refresh

