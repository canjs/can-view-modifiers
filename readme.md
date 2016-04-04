# can-view-modifiers (DEPRECATED)

*The can-view-modifiers plugin is deprecated*

[![Build Status](https://travis-ci.org/canjs/can-view-modifiers.png?branch=master)](https://travis-ci.org/canjs/can-view-modifiers)

Use jQuery modifiers to render views

## Overview

The can/view/modifiers plugin extends the jQuery view modifiers

* jQuery.fn.after
* jQuery.fn.append
* jQuery.fn.before
* jQuery.fn.html
* jQuery.fn.prepend
* jQuery.fn.replaceWith
* jQuery.fn.text

to render a [can.view](http://canjs.com/docs/can.view.html). When rendering a view you call the view modifier the same way
as can.view with the view name or id as the first, the data as the second and the optional
success callback (to load the view asynchronously) as the third parameter.
For example, you can render a template from *todo/todos.ejs* looking like this:

	<% for(var i = 0; i < this.length; i++ ){ %>
	  <li><%= this[i].name %></li>
	<% } %>

By calling the [can.prototype.jQuery.fn.html html] modifier on the `#todos` element like this:

    can.$('#todos').html('todo/todos.ejs', [
        { name : 'First Todo' },
        { name : 'Second Todo' }
	]);

__Note:__ You always have to provide the data (second) argument to render a view, otherwise the standard jQuery
modifier will be used. If you have no data to render pass an empty object:

	$('#todos').html('todo/todos.ejs', {});
	// Render todo/todos.ejs wit no data

### Deferreds

Additionally it is also possible to pass a [can.Deferred] as a single parameter to any view modifier. Once
the deferred resolves the result will be rendered using that modifier. This can be used to easily request
and render static content. The following example inserts the content of _content/info.html_ after the `#todos` element:

	can.$('#todos').after(can.ajax({
		url : 'content/info.html'
	}));

### API

For API details, see `src/can-view-modifiers.js`

## Usage

### ES6 use

With StealJS, you can import this module directly in a template that is autorendered:

```js
import plugin from 'can-view-modifiers';
```

### CommonJS use

Use `require` to load `can-view-modifiers` and everything else
needed to create a template that uses `can-view-modifiers`:

```js
var plugin = require("can-view-modifiers");
```

## AMD use

Configure the `can` and `jquery` paths and the `can-view-modifiers` package:

```html
<script src="require.js"></script>
<script>
	require.config({
	    paths: {
	        "jquery": "node_modules/jquery/dist/jquery",
	        "can": "node_modules/canjs/dist/amd/can"
	    },
	    packages: [{
		    	name: 'can-view-modifiers',
		    	location: 'node_modules/can-view-modifiers/dist/amd',
		    	main: 'lib/can-view-modifiers'
	    }]
	});
	require(["main-amd"], function(){});
</script>
```

### Standalone use

Load the `global` version of the plugin:

```html
<script src='./node_modules/can-view-modifiers/dist/global/can-view-modifiers.js'></script>
```

## Contributing

### Making a Build

To make a build of the distributables into `dist/` in the cloned repository run

```
npm install
node build
```

### Running the tests

Tests can run in the browser by opening a webserver and visiting the `test.html` page.
Automated tests that run the tests from the command line in Firefox can be run with

```
npm test
```
