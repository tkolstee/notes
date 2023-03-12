
[Sass: Sass Basics](https://sass-lang.com/guide)

## Installing
[https://sass-lang.com/install](https://sass-lang.com/install)

Apps
- Paid:
	- Mac: [CodeKit](https://codekitapp.com/), [Hammer](http://hammerformac.com/), [LiveReload](http://livereload.com/), [Prepros](https://prepros.io/) 
	- Windows: [LiveReload](http://livereload.com/), [Prepros](https://prepros.io/)
	- Linux: [Prepros](https://prepros.io/)
- Free
	- Windows, Linux, Mac: [Scout-App](http://scout-app.io/)

Libraries
- [Java](https://mvnrepository.com/artifact/de.larsgrefer.sass), including [Gradle](https://docs.freefair.io/gradle-plugins/current/reference/#_embedded_sass) and [Maven](https://github.com/HebiRobotics/sass-cli-maven-plugin) plugins.
- [Ruby](https://github.com/ntkme/sass-embedded-host-ruby#readme)
- [Swift](https://github.com/johnfairh/swift-sass#readme)

CLI
- `npm install -g sass`
- `brew install sass/sass/sass`
- `choco install sass`

## Basics

Complies to CSS files: `sass input.scss output.css`

Two syntaxes:
- `.scss` (more common, superset of CSS)
- `.sass` indentation and newlines instead of braces and semicolons

Adds nesting, mixins, inheritance, etc.
Watch and recompile:
- `sass --watch input.scss output.css`
- `sass --watch app/sass:public/stylesheets`

### Variables
Denoted with $
```SCSS
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
	font: 100% $font-stack;
	color: $primary-color;
}
```
```
/* SASS Syntax */

$font-stack: Helvetica, sans-serif
$primary-color: #333

body 
	font: 100% $font-stack 
	color: $primary-color
```

## Nesting
Provides a visual cue for hierarchy of nested tags
```SCSS
nav {
	ul {
		margin: 0;
		padding: 0;
		list-style: none;
	}
	li { 
		display: inline-block;
	}
}
```

```
/* SASS Syntax */
nav
	ul
		margin: 0
		padding: 0
		list-style: none
	li 
		display: inline-block
```

## Partials and @use

Name files with leading underscore: `_partial.scss`. 
These will not be generated into CSS files but can be included with `@use`

```CSS
/* base.scss */
$font-stack: Helvetica, sans-serif;
$primary-color: #333;
body {
	font: 100% $font-stack;
	color: $primary-color;
}

/* styles.scss */
@use 'base';
.inverse { 
	background-color: base.$primary-color;
	color: white;
}
```

## Mixins
```SCSS
@mixin theme($theme: DarkGray) { 
	background: $theme; 
	box-shadow: 0 0 1px rgba($theme, .25);
	color: #fff;
} 
.info    { 
	@include theme;
} 
.alert   {
	@include theme($theme: DarkRed);
}
.success {
	@include theme($theme: DarkGreen);
}

```


## Extend / Inheritance
```SCSS
/* Will print because %message-shared is extended. */
%message-shared {
	border: 1px solid #ccc;
	padding: 10px;
	color: #333;
} 

/* won't print because %equal-heights is never extended. */
%equal-heights {
	display: flex;
	flex-wrap: wrap;
}
.message { @extend %message-shared; }
.success { 
	@extend %message-shared;
	border-color: green;
} 
.error {
	@extend %message-shared;
	border-color: red;
}
.warning {
	@extend %message-shared;
	border-color: yellow;
}
```

Compiles to CSS:
```CSS
/* 
will print because
%message-shared is extended.
*/
.message, .success, .error, .warning {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```

## Operators
```SCSS
@use "sass:math";

.container {
  display: flex;
}

article[role="main"] {
  width: math.div(600px, 960px) * 100%;
}

aside[role="complementary"] {
  width: math.div(300px, 960px) * 100%;
  margin-left: auto;
}
```
Compiles to CSS:
```CSS
.container {
  display: flex;
}

article[role="main"] {
  width: 62.5%;
}

aside[role="complementary"] {
  width: 31.25%;
  margin-left: auto;
}
```

