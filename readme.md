# can-view-modifiers

[![Build Status](https://travis-ci.org/canjs/can-view-modifiers.png?branch=master)](https://travis-ci.org/canjs/can-view-modifiers)

Use jQuery modifiers to render views

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
