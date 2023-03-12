`package.json`
```json
{
  "name": "my-vue-app",
  "version": "0.1.0",
  "dependencies": {
    "vue": "^3.2.45",
    "core-js": "3.26.1",
    "@vue/compiler-sfc": "^3.2.45",
    "@vue/cli-service": "^5.0.8"
  }
}
```
Run `npm install` to install packages specified here.

`core-js` is used to emulate new features in older version of the JS engine (transpiling)
`@vue/compiler-sfc` is used to compile VueJS components.
`@vue/cli-service` provides CLI commands to compile and run apps.

`public/index.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Cool Vue App</title>
  </head>
  <body>
    <!-- Container for the rendered app -->
    <div id="app"></div>  
  </body>
</html>
```
Contains a single `div` element with a given ID - by convention `app`.
This is where the app will be rendered.


`src/App.vue`
```vue
<!-- Template section defines HTML rendered in container -->
<template>
  <div>
    <h1>My Cool Vue App</h1>
    <button>Add Task</button>
  </div>
</template>

<!-- Script section defines JS code for app -->
<script>
  export default {
    name: "App"
  }
</script>

<!-- Style section defines CSS rules -->
<style>
</style>
```
Represents one component or "screen"
Contains sections:
- `template` with HTML
- `script` with JS code
- `style` with CSS

exports a symbolic name - by convention matches name of file.


`src/main.js`
```javascript
// createApp function will be used below.
import { createApp } from 'vue'

// This is the app that we created
import App from './App.vue'

// This creates the imported app and renders it
// in the container by 'id' attribute.
createApp(App).mount('#app')
```
- Imports the symbol exported from the `.vue` file (`App`)
- Creates the app
- Mounts the app to the element in `index.html` (`#app`)

## Running the App
`./node_modules/@vue/cli-service/bin/vue-cli-service.js serve`
or
`./node_modules/.bin/cli-service serve`

	  App running at:
	  - Local:   http://localhost:8080/ 
	  - Network: http://192.168.1.74:8080/
	
	  Note that the development build is not optimized.
	  To create a production build, run npm run build.

Also we can add an alias to package.json (See [[000 Topics/JS/npm]]):
```json
{
  "scripts": {
	  "serve": "vue-cli-service serve"
  }
}
```

## Nested Components

We can create child elements with more Vue components.


To the template in our main app vue file, add a custom HTML element with a capital:
`App.vue`:
```javascript
<template>
	<div class="container">
		<Header />
	</div>
</template>
// ... script, style...
```

Add the new element as a new vue file, exporting the same name.
`Header.vue`
```javascript
<template>
	<header>
		<h1>My Cool Vue App</h1>
	</header>
</template>
<script>
	export default {
		name: 'Header'
	}
</script>
<style>...</style>
```

To the script component, import the nested component and add the component to the export statement.
`App.vue`
```html
<script>
  import Header from './Header.vue'
  export default {
    name: "App",
    components: { Header }
  }
</script>
```

## Passing Parameters to Components

```html
<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>
```

```HTML
<template>
  <div class="container">
    <Header title="Vue App" />
  </div>
</template>
```

```html
<script>
  export default {
    name: 'Header',
    props: { title: String }
  }
</scipt>
```

### Style information in Parameters

Add properties to `script/export default/props` and reference them using `:style` on HTML tags:

`Header.vue`
```HTML
<template>
	<h1 :style="{ background: bgcolor, color: textcolor }">foo</h1>
<template>
```
`Header.vue`
```JavaScript
<script>
	props: {
		'color': String,
		'bgcolor': String
	}
</script>
```

`App.vue`
```HTML
<template>
	<Header color="lightblue" bgcolor="darkblue">
</template>
```


## Event Handling

`Header.vue` - TEMPLATE
```HTML
<button @click="handleClick()">
```

`Header.vue` - SCRIPT
```Javascript
methods: {
	handleClick() {
		console.log("Button clicked.")
	}
}
```

## Passing data with v-bind (:)
```HTML
<img :src=myimg>
```
```JS
import image from "./profileimg.jpg"
export default {
    // ...
	data() {
		return {
			myimg: image
		}
	}
}
```


## Declaring Methods with v-on (@)
Define "methods" attribute to export:
```javascript
export default {
  // ...
  methods: {
	  myfunc() { console.log('1'); },
	  myfunc2() { console.log('2'); }
  }
}
```

```HTML
<button @click="myfunc">
```

## Importing VanillaJS Libs

In Script section of vue file:
```javascript
import validator from '../node_modules/validator/validator.js'
```
You can now use those methods from within other JS methods

## Hiding and showing elements
```HTML
<div v-show="!isEditMode">
```

```javascript
export default {
  // ...
  data() {
	  isEditMode: false
  },
  methods() {
	  handleEditButtonPress() { this.isEditMode = true }
  }
}
```

## Binding variables to HTML elements
```HTML
<!-- Within text content of elements: -->
<p>{{ email }}</p>

<!-- Within a HTML attribute --->
<input type="text" :placeholder=email />

<!-- Two-way binding -->
<input type="text" v-model=email />
```


## Sending Info to Backend:
```javascript
// If inside a function the function should be marked async
var payload = { task: taskname }
var req = { 
	method: "POST",
	body: JSON.stringify(payload),
	headers: {
		"Accept": "application/json",
		"Content-Type": "application/json"
	}
}
var res = await fetch('save-task', req)
jsonRes = await res.json()
```


